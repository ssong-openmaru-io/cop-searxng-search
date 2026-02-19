# SearXNG Kubernetes Manifests

이 디렉토리는 SearXNG 메타 검색 엔진을 Kubernetes 환경에 배포하기 위한 매니페스트를 제공합니다.
Ingress(NGINX) 환경에서 정상 동작하도록 X-Forwarded-For 처리, trusted_proxies, Valkey/Redis 연동 등을 포함한 운영 기준 설정을 반영합니다.
 
## 구성 요소
```
 /manifests
 ├── configmap.yaml      # SearXNG settings.yml
 ├── deployment.yaml     # SearXNG Deployment
 ├── service.yaml        # ClusterIP Service 
 └── ingress.yaml        # NGINX Ingress
```

## 아키텍처
```
Client
  ↓
NGINX Ingress
  ↓
Service (ClusterIP)
  ↓
SearXNG Pod
```
AI Agent 환경에서는 내부 서비스 호출을 권장합니다.
```
Flowise / LangChain
      ↓
http://searxng.namespace.svc.cluster.local
```