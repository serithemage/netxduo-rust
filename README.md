# NetXDuo Rust Port (RustXDuo)

이 프로젝트는 Eclipse ThreadX NetX Duo TCP/IP 네트워크 스택을 Rust 프로그래밍 언어로 포팅하는 작업입니다. Task Master를 활용한 체계적인 접근 방식으로 바이브 코딩(Vibe Coding)을 통해 C 코드베이스를 Rust로 변환합니다.

## 프로젝트 개요

NetXDuo는 임베디드 실시간 및 IoT 애플리케이션을 위한 산업용 TCP/IP 네트워크 스택으로, IPv4와 IPv6를 모두 지원합니다. 이 포팅 프로젝트는 원본 C 구현의 모든 기능을 유지하면서 Rust의 메모리 안전성, 동시성 안전성, 현대적인 언어 기능을 활용합니다.

### 주요 목표

- Rust의 안전성 기능을 활용하여 메모리 및 동시성 버그 제거
- 원본 C 구현과 비교하여 성능 유지 또는 향상
- 모든 기존 프로토콜 및 기능 지원
- 포괄적인 문서화 및 예제 제공
- Clean Architecture와 SOLID 원칙을 따르는 유지보수 가능한 코드베이스 구축
- 철저한 테스트 구현 (단위 테스트, 통합 테스트, 벤치마크)

## Task Master를 활용한 개발 접근 방식

이 프로젝트는 Task Master를 사용하여 체계적인 개발 워크플로우를 구현합니다. Task Master는 복잡한 프로젝트를 관리 가능한 작업으로 분해하고, 의존성을 추적하며, 진행 상황을 모니터링하는 도구입니다.

### 작업 구조

프로젝트는 다음과 같은 주요 작업으로 구성되어 있습니다:

1. **프로젝트 설정 및 저장소 구조**
   - Rust 워크스페이스 구조 설정
   - 빌드 구성 및 의존성 관리
   - 문서화 및 테스트 인프라 구축

2. **핵심 데이터 구조 및 메모리 관리**
   - 패킷 표현 및 버퍼 관리
   - 네트워크 주소 추상화
   - 스레드 안전 버퍼 관리

3. **네트워크 인터페이스 추상화**
   - 하드웨어 추상화 계층
   - 드라이버 인터페이스
   - 인터페이스 관리 시스템

4. **프로토콜 구현**
   - IPv4 및 IPv6 프로토콜
   - TCP 및 UDP 전송 프로토콜
   - ARP, ICMP 등 기본 프로토콜
   - HTTP, MQTT, DHCP 등 상위 프로토콜

5. **보안 구현**
   - TLS/DTLS 구현
   - 암호화 라이브러리
   - 인증서 관리

### 개발 워크플로우

```
1. 작업 분석 및 복잡도 평가 (task-master analyze-complexity)
2. 작업 세분화 (task-master expand --id=<id>)
3. 테스트 작성 (TDD 접근 방식)
4. 구현 및 리팩토링
5. 작업 완료 표시 (task-master set-status --id=<id> --status=done)
6. 다음 작업 선택 (task-master next)
```

## 프로젝트 구조

```
netxduo-rust/
├── netxduo-core/           # 핵심 데이터 구조 및 기본 기능
├── netxduo-protocols/      # 네트워크 프로토콜 구현
├── netxduo-security/       # 보안 및 암호화 기능
├── netxduo-platform/       # 플랫폼 추상화 및 드라이버
├── examples/               # 예제 애플리케이션
├── tests/                  # 통합 테스트
├── docs/                   # 문서화
└── tasks/                  # Task Master 작업 정의
```

## 시작하기

### 필수 도구

- Rust 및 Cargo (최신 안정 버전)
- Task Master CLI (`npm install -g claude-task-master`)
- 임베디드 개발을 위한 도구:
  - Arm GNU 툴체인 (arm-none-eabi)
  - LLVM/Clang (최신 버전)
  - CMake 3.0 이상

### 프로젝트 설정

```bash
# 저장소 클론
git clone --recursive https://github.com/your-org/netxduo-rust.git
cd netxduo-rust

# 작업 목록 확인
task-master list

# 다음 작업 확인
task-master next

# 작업 확장
task-master expand --id=<id> --research
```

## 테스트 전략

- 모든 구성 요소에 대한 단위 테스트
- 프로토콜 상호 작용을 위한 통합 테스트
- 프로토콜 사양에 대한 적합성 테스트
- 성능 벤치마크
- 보안 중요 구성 요소에 대한 퍼즈 테스트
- 다른 구현과의 상호 운용성 테스트

## 기여하기

기여는 언제나 환영합니다! 다음 단계를 따라주세요:

1. 이슈 생성 또는 기존 이슈 확인
2. 포크 및 브랜치 생성
3. 코드 작성 및 테스트
4. PR 제출

모든 기여는 [CONTRIBUTING.md](./CONTRIBUTING.md)에 명시된 지침을 따라야 합니다.

## 라이선스

이 프로젝트는 원본 NetXDuo와 동일한 라이선스 조건을 따릅니다. 자세한 내용은 [LICENSE.txt](./LICENSE.txt) 파일을 참조하세요.

## 원본 NetXDuo 프로젝트

이 프로젝트는 다음 Eclipse ThreadX NetX Duo 프로젝트를 기반으로 합니다:
[https://github.com/eclipse-threadx/netxduo](https://github.com/eclipse-threadx/netxduo)

원본 프로젝트에 대한 자세한 정보는 [Eclipse ThreadX 문서](https://github.com/eclipse-threadx/rtos-docs)를 참조하세요.
