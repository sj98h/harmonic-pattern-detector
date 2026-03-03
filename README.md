# ◈ HARMONIC PATTERN DETECTOR

> 피보나치 비율 입력 → 하모닉 패턴 자동 감지  
> Google Sheets as a backend · PWA · 오차범위 실시간 조정

---

## ✦ Features

- **63개 패턴 감지** — 근본 / 근본+ / 사파 / 반전형 / 짬통 전 카테고리
- **오차범위 슬라이더** — 0~10% 실시간 조정
- **Google Sheets DB** — 시트 수정하면 앱에 즉시 반영
- **PWA** — 홈 화면에 앱으로 설치, 오프라인 캐시 지원
- **강력 새로고침** — 서비스워커 캐시 초기화 후 최신 데이터 fetch

---

## ✦ Stack

```
Google Sheets  →  CSV fetch  →  Vanilla JS  →  GitHub Pages
                                                     ↓
                                               PWA (sw.js)
```

---

## ✦ Project Structure

```
├── index.html      # 앱 본체 (UI + 감지 로직)
├── sw.js           # Service Worker (캐시 전략)
├── manifest.json   # PWA 메타 설정
├── icon-192.png    # 앱 아이콘
└── icon-512.png
```

---

## ✦ Setup

### 1. Google Sheets 설정

패턴 데이터 시트를 **링크가 있는 사용자 → 뷰어** 로 공유 설정

시트 컬럼 순서는 아래와 같아야 합니다:

```
category | name | minXB | maxXB | minAC | maxAC | minBD | maxBD | minXD | maxXD | comment
```

### 2. index.html 설정

```javascript
const SHEET_ID  = 'YOUR_SHEET_ID';  // 시트 URL /d/XXXXX/edit 의 XXXXX
const SHEET_GID = '0';              // 탭 우클릭 → 시트 ID 복사
```

### 3. GitHub Pages 배포

```
Settings → Pages → Branch: main / root → Save
```

---

## ✦ Pattern Categories

| 카테고리 | 설명 |
|---------|------|
| 근본 | Bat, Gartley, Butterfly, Crab 등 클래식 패턴 |
| 근본+ | Shark, Cypher 등 확장 패턴 |
| 사파 | Navarro, Nen star, Swan 계열 |
| 반전형 | Anti 패턴 (A Bat, A Gartley 등) |
| 짬통 | Partizan, TOTAL, BG 계열 등 기타 |

---

## ✦ Service Worker Cache Strategy

- `docs.google.com` 요청 → **Network only** (항상 최신 데이터)
- 나머지 앱 파일 → **Cache first** (오프라인 지원)
- `↺` 버튼 → 전체 캐시 삭제 후 강제 재fetch

---

## ✦ License

Private. All rights reserved.
