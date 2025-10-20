# 🐾 Spring PetClinic Microservices – Helm Deployment Guide

Triển khai dự án **Spring PetClinic Microservices** trên **Kubernetes** bằng **Helm Chart**.

---

## 🧩 Giới thiệu

Dự án **Spring PetClinic Microservices** là phiên bản microservice của ứng dụng PetClinic, được xây dựng bằng **Spring Boot**, **Spring Cloud**, và **Eureka Discovery**.  
Link gốc: [spring-petclinic-microservices](https://github.com/spring-petclinic/spring-petclinic-microservices)

Hướng dẫn này giúp bạn deploy toàn bộ hệ thống bằng Helm trên Kubernetes.

---

## ⚙️ Yêu cầu

- Kubernetes Cluster (Minikube, Kind, GKE, EKS, AKS, …)
- `kubectl` và `helm` (v3 trở lên)
- Docker (nếu bạn muốn build image)
- (Tuỳ chọn) Registry riêng nếu muốn push image tự build
- (Tuỳ chọn) Persistent DB (MySQL hoặc PostgreSQL)

---

## 🐳 Build & Push Docker Images (tuỳ chọn)

Nếu bạn muốn build image của riêng mình:

```bash
./mvnw clean install -P buildDocker

# Sau đó push lên registry riêng của bạn
export REPOSITORY_PREFIX=your-registry/petclinic
./scripts/tagImages.sh && ./scripts/pushImages.sh

