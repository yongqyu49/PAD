# PAD (Personal Art Display)

PAD는 사용자들이 자신의 작품과 게시글을 공유하고 소통할 수 있는 커뮤니티 게시판 플랫폼입니다.

## 📋 프로젝트 개요

PAD는 React 기반 프론트엔드와 Spring Boot 기반 백엔드로 구성된 풀스택 웹 애플리케이션입니다. 사용자들은 게시글을 작성하고, 카테고리별로 탐색하며, 다른 사용자들과 소통할 수 있습니다.

## ✨ 주요 기능

### 회원 관리
- 📝 회원가입 및 로그인
- 👤 프로필 관리 (내 정보 조회/수정)
- 🔐 Spring Security 기반 인증/인가
- 🔑 세션 기반 사용자 관리
- ❌ 회원 탈퇴

### 게시판 기능
- 📄 게시글 작성, 조회, 수정, 삭제 (CRUD)
- 🎨 CKEditor 기반 리치 텍스트 에디터
- 🖼️ 이미지 업로드 및 관리
- 📂 카테고리별 게시글 분류
- 📱 페이지네이션 지원
- 🔍 최신 게시글 조회

### 소셜 기능
- ⭐ 즐겨찾기 (북마크) 추가/취소
- 📊 내 게시글 및 즐겨찾기 관리
- 📢 공지사항 시스템

### 사용자 인터페이스
- 📱 반응형 디자인
- 🎠 React Slick 캐러셀
- 🎨 직관적인 사용자 경험

## 🛠 기술 스택

### Frontend
- **React** 18.2.0 - UI 라이브러리
- **Redux Toolkit** - 상태 관리
- **React Router DOM** 6.20.0 - 라우팅
- **CKEditor 5** - 리치 텍스트 에디터
- **React Slick** - 캐러셀 슬라이더
- **Create React App** - 프로젝트 보일러플레이트

### Backend
- **Spring Boot** 3.2.1-SNAPSHOT - 백엔드 프레임워크
- **Java** 17 - 프로그래밍 언어
- **Spring Security** - 인증/인가
- **MyBatis** 3.0.3 - SQL 매핑 프레임워크
- **Spring JDBC** - 데이터베이스 연동
- **Lombok** - 코드 간소화

### 데이터베이스
- **Oracle Database** 21c (with Wallet 지원)

### 테스트용 백엔드 (개발 환경)
- **Node.js + Express** - 테스트 서버
- **MySQL2** - 개발용 데이터베이스
- **Socket.io** - 실시간 통신
- **Multer** - 파일 업로드

## 📁 프로젝트 구조

이 프로젝트는 Git 서브모듈을 사용하여 프론트엔드와 백엔드를 분리 관리합니다.

```
PAD/
├── front/                  # React 프론트엔드 서브모듈 (PAD_FE)
│   ├── pad/               # React 애플리케이션
│   │   ├── src/
│   │   │   ├── Front/     # UI 컴포넌트
│   │   │   │   ├── Body/  # 페이지 컴포넌트
│   │   │   │   ├── Footer/
│   │   │   │   └── Menubar/
│   │   │   ├── Redux/     # Redux 스토어
│   │   │   └── App.js
│   │   └── package.json
│   └── node_server/       # 테스트용 Express 서버
│
├── PAD_BE/                # Spring Boot 백엔드 서브모듈
│   ├── src/
│   │   ├── main/java/com/pad/dev/
│   │   │   ├── controller/    # REST API 컨트롤러
│   │   │   ├── service/       # 비즈니스 로직
│   │   │   ├── dao/           # 데이터 접근 계층
│   │   │   └── vo/            # Value Objects
│   │   └── resources/
│   │       └── mapper/        # MyBatis XML 매퍼
│   └── build.gradle
│
└── README.md              # 이 파일
```

## 🚀 설치 및 실행 방법

### 사전 요구사항

- **Java 17** 이상
- **Node.js** v14 이상 및 npm
- **Gradle** 7.x 이상
- **Oracle Database** 21c (프로덕션) 또는 **MySQL** (개발)
- **Git**

### 1. 저장소 클론 및 서브모듈 초기화

```bash
# 저장소 클론
git clone https://github.com/yongqyu49/PAD.git
cd PAD

# 서브모듈 초기화 및 업데이트
git submodule update --init --recursive
```

### 2. 백엔드 설정 및 실행

#### Oracle 데이터베이스 설정
1. Oracle Database 21c 설치 및 구성
2. Oracle Wallet 파일 준비
3. `PAD_BE/src/main/resources/application.yml` 파일 생성:

```yaml
spring:
  datasource:
    url: jdbc:oracle:thin:@<your-database-url>
    username: <your-username>
    password: <your-password>
```

#### 백엔드 실행

```bash
cd PAD_BE

# 빌드
./gradlew build

# 실행
./gradlew bootRun
```

백엔드 서버는 **http://localhost:8800** 에서 실행됩니다.

### 3. 프론트엔드 설정 및 실행

```bash
cd front/pad

# 의존성 설치
npm install

# 개발 서버 실행
npm start
```

프론트엔드는 **http://localhost:3000** 에서 실행됩니다.

### 4. (선택사항) 테스트용 Node.js 백엔드 실행

개발 환경에서 Oracle 대신 MySQL을 사용하는 경우:

```bash
cd front/node_server

# 의존성 설치
npm install

# MySQL 데이터베이스 설정 후 실행
npm start
```

테스트 서버는 **포트 7223**에서 실행됩니다.

## 📡 주요 API 엔드포인트

### 회원 관리 (`/proxy/member`)

| 메서드 | 엔드포인트 | 설명 |
|--------|-----------|------|
| POST | `/proxy/member/SignUp` | 회원가입 |
| POST | `/proxy/member/SignIn` | 로그인 |
| POST | `/proxy/member/Logout` | 로그아웃 |
| POST | `/proxy/member/MyInfo` | 내 정보 조회 |
| POST | `/proxy/member/Update` | 회원정보 수정 |
| POST | `/proxy/member/Delete` | 회원 탈퇴 |
| POST | `/proxy/member/session` | 세션 정보 조회 |

### 게시판 (`/proxy/board`)

| 메서드 | 엔드포인트 | 설명 |
|--------|-----------|------|
| POST | `/proxy/board` | 게시글 목록 조회 (페이징) |
| POST | `/proxy/board/category` | 카테고리별 게시글 조회 |
| POST | `/proxy/board/watch` | 게시글 상세 조회 |
| POST | `/proxy/board/Write` | 게시글 작성 |
| POST | `/proxy/board/Update` | 게시글 수정 |
| POST | `/proxy/board/Delete` | 게시글 삭제 |
| POST | `/proxy/board/image` | 이미지 업로드 |
| POST | `/proxy/board/latestBoard` | 최신 게시글 조회 |
| POST | `/proxy/board/myBoard` | 내 게시글 목록 |

### 즐겨찾기

| 메서드 | 엔드포인트 | 설명 |
|--------|-----------|------|
| POST | `/proxy/member/fav` | 즐겨찾기 추가 |
| POST | `/proxy/member/favCancle` | 즐겨찾기 취소 |
| POST | `/proxy/member/MyFavorite` | 내 즐겨찾기 목록 |

### 공지사항 (`/proxy/notice`)

| 메서드 | 엔드포인트 | 설명 |
|--------|-----------|------|
| POST | `/proxy/notice/mainNotice` | 공지사항 목록 조회 |

## 🔧 환경 설정

### 프론트엔드 프록시 설정

`front/pad/package.json`에서 백엔드 서버 주소를 설정합니다:

```json
{
  "proxy": "http://localhost:8800"
}
```

### 백엔드 포트 설정

기본 포트는 **8800**입니다. 변경이 필요한 경우 `application.yml`에서 수정하세요.

### 세션 설정

- 세션 유지 시간: 1800초 (30분)
- 세션 기반 사용자 인증
- 로그아웃 시 세션 무효화

## 🔐 보안

- **Spring Security**를 통한 인증/인가 처리
- **PasswordEncoder**를 사용한 비밀번호 암호화
- 세션 기반 사용자 인증
- CORS 설정 지원

## 📦 빌드 및 배포

### 프론트엔드 빌드

```bash
cd front/pad
npm run build
```

빌드된 파일은 `build/` 디렉토리에 생성됩니다.

### 백엔드 빌드

```bash
cd PAD_BE
./gradlew build
```

WAR 파일은 `build/libs/` 디렉토리에 생성됩니다.

## 📚 추가 정보

### 서브모듈 저장소

- **프론트엔드**: [PAD_FE](https://github.com/yongqyu49/PAD_FE)
- **백엔드**: [PAD_BE](https://github.com/yongqyu49/PAD_BE)

### 개발 가이드

각 서브모듈의 README.md 파일에서 더 자세한 개발 가이드를 확인할 수 있습니다.

