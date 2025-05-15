<p align="center">
  <img src="https://github.com/user-attachments/assets/21db789f-3ef1-4497-80a7-cde351fcd19a" alt="BookKing 배너" width="1000" height="400"/>
</p>
<hr>

# 📚 BookKing – 스마트 도서 검색 및 추천 서비스

**프로젝트 기간**: 2025.04 ~ 2025.05  
**담당 역할**: 백엔드 개발 (리뷰/주문/키워드 기능, 모니터링, 테스트 문서)  
**팀 구성**: 백엔드 개발자 5인 (프론트엔드 미구현)  
**GitHub**: [https://github.com/polaris65b/bookKing](https://github.com/polaris65b/bookKing)

---

## 🔍 프로젝트 개요

사용자의 독서 경험을 향상시키기 위한 **도서 검색·추천 백엔드 API 서비스**입니다.  
단순 키워드 검색을 넘어, 사용자 로그 기반 키워드 추천(AI), 도서 리뷰, 주문 관리, 모니터링 등 기능을 제공합니다.

---

## 🧩 담당한 주요 기능

### ✅ 리뷰 기능 (Review)
- 도서 구매자만 리뷰 작성 가능하도록 검증 로직 구현
- 리뷰 중복 방지: 한 도서당 한 번만 작성 가능 (수정 가능)
- QueryDSL 기반 리뷰 조회 성능 최적화
- 단위 테스트 및 예외 케이스 처리 포함

### ✅ 주문 기능 (Order)
- 사용자의 도서 구매 내역 저장 및 조회 API 구현
- 리뷰 작성 조건(구매 여부)과 연동하여 역할 분리 처리

### ✅ 키워드 추천 기능 (Keyword AI)
- 사용자의 구매 이력을 기반으로 AI 키워드 추천
- **OpenAI API** 활용 (GPT 모델)
- 자체 AI 모델(MCP) 도입과의 비교 분석 후 **비용·개발 효율성** 측면에서 API 방식 채택
- 추후 사용자 증가 시 MCP로의 전환을 고려한 구조 설계

---

## 📈 테스트 및 품질 관리

- Google Sheets 기반 테스트 시나리오 작성
- 기능별 입력값/예상 출력값/예외 처리 등 명확하게 문서화
- JUnit5 및 Mockito 기반 테스트 코드 작성
- 일부 기능은 JMeter로 성능 테스트 진행

---

## ⚙️ 모니터링 구축 및 인프라 전환 경험

### ✅ 환경 변화
- 단일 서버 환경 → 다중 EC2 서버 → AWS Fargate 환경으로 전환
- 초기엔 **Node Exporter + Prometheus** 구성

### ✅ 문제 해결
- EC2 → Fargate 전환 시, Prometheus의 타깃 수집 불안정 문제 발생  
→ `prometheus-ecs-discovery` + `file_sd_configs` 설정으로 Fargate Task 자동 수집 처리  
→ Prometheus, Grafana 대시보드로 JVM 메트릭, API 응답 속도 등 시각화 구성

---

## 🧠 기술적 의사결정 및 성장 포인트

- **AI 추천 전략**:  
  MCP와 API 방식 비교 → API는 초기비용 낮음, 운영비 예측 가능 → API 채택  
  추후 사용량 증가 시 MCP로 전환 가능성 고려한 설계

- **모니터링 전략**:  
  서버 환경 변화에 따라 유연하게 대응하며 **실시간 서비스 운영 안정성 확보**

---

## 🛠 사용 기술 스택

| 분류         | 기술 |
|--------------|------|
| Language     | Java 17 |
| Framework    | Spring Boot |
| Database     | MySQL, Redis |
| 검색 & AI    | Elasticsearch, OpenAI API |
| Infra & DevOps | AWS EC2,
