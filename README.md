## MSA Sample Guide
## 소개
본 Repository는 K-Paas 컨테이너플랫폼을 활용해 **MSA(Micro Service Architecture)** 샘플 프로젝트를 구축하고 활용할 수 있도록 구성되어있다.
> 컨테이너플랫폼 파이프라인 서비스를 이용해 해당 샘플을 배포하는 방법은 아래 가이드를 참고한다.  
[[Pipeline 서비스 사용 가이드]](https://github.com/K-PaaS/container-platform/blob/master/use-guide/pipeline/cp-pipeline-use-guide.md)


<br>

## 구성도
<kbd>
  <img src="https://github.com/K-PaaS/msa-sample-gateway/assets/67575226/2541af60-7868-4ef5-9a74-6b7758227b10" width="600px">
</kbd>

<br><br>

| component          | Desc                      | NodePort |
|--------------------|---------------------------|:--------:|
| msa-sample-api     | Msa Sample API 기능         |  30010   |
| msa-sample-sd-api  | Msa Sample Side API 기능    |  30014   |
| msa-sample-ui      | Msa Sample UI 기능          |  30011   |
| msa-sample-gateway | Msa Sample API Gateway 기능 |  30012   |

<br> 
<br> 


## 프로젝트
- msa-sample-api
  + https://github.com/K-PaaS/msa-sample-api.git
- msa-sample-sd-api
  + https://github.com/K-PaaS/msa-sample-sd-api.git
- msa-sample-ui
  + https://github.com/K-PaaS/msa-sample-ui.git 
- msa-sample-gateway
  + https://github.com/K-PaaS/msa-sample-gateway.git



<br>

## 배포
### 1. 환경변수 Configmap 생성
MSA 구성 배포 전 **Kubernetes Master Node**에서 환경변수를 위한 **configmap**을 생성한다.

- `{K8S_MASTER_NODE_IP}` 값 변경 필요
> [[configmap.yml]](resource/configmap.yml)
>

```
kubectl create -f configmap.yml
``` 

<br>

### 2. MSA 구성 배포
**컨테이너플랫폼 파이프라인 서비스**를 통해 MSA 구성 배포 시 아래 yml로 변경하여 배포한다.
#### MSA API 배포
> [deployment.yml](api/deployment.yml) <br>
> [service.yml](api/service.yml)

#### MSA SD-API 배포
> [deployment.yml](sd-api/deployment.yml) <br>
> [service.yml](sd-api/service.yml)

#### MSA UI 배포
> [deployment.yml](ui/deployment.yml) <br>
> [service.yml](ui/service.yml)

#### Gateway 배포
> [deployment.yml](gateway/deployment.yml) <br>
> [service.yml](gateway/service.yml)

<br>

## 접속
Gateway를 통해 UI에 접속한다. <br><br>
**접속 URL** : `{K8S_MASTER_NODE_IP}:30011/hello` 