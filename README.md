# AI 오목 학생 프론트엔드

Cloudflare Pages에 배포하는 학생용 정적 웹입니다. Python 알고리즘 실행은 별도로 배포된 백엔드가 담당합니다.

## 파일

- `index.html`: 학생 사이트 전체 화면과 동작
- `config.js`: 실제 Supabase·백엔드 주소 설정
- `config.example.js`: 설정 예시

## 처음 설정

`config.js`에서 다음 세 값을 실제 값으로 변경합니다.

```js
const SUPABASE_URL = "https://YOUR_PROJECT.supabase.co";
const SUPABASE_KEY = "YOUR_SUPABASE_PUBLISHABLE_KEY";
const BACKEND_URL = "https://YOUR_BACKEND.onrender.com";
```

`BACKEND_URL`에는 Render 기본 주소만 입력하며 `/health`, `/api`, 마지막 `/`는 넣지 않습니다.

## VS Code에서 실행 확인

정적 파일이므로 VS Code의 Live Server 확장 프로그램으로 `index.html`을 열 수 있습니다. 로컬 주소를 백엔드의 `ALLOWED_ORIGINS`에 추가하지 않았다면 화면은 열려도 API 요청은 CORS로 차단될 수 있습니다.

## GitHub 관리

1. VS Code에서 이 폴더를 엽니다.
2. GitHub 저장소를 생성하거나 기존 학생 프론트엔드 저장소에 연결합니다.
3. 세 파일을 커밋하고 푸시합니다.
4. Cloudflare Workers & Pages에서 해당 GitHub 저장소를 연결합니다.

별도 빌드 과정은 필요하지 않습니다. 배포 루트에 `index.html`과 `config.js`가 있어야 합니다.

## 주의

- `service_role`, `sb_secret` 키는 프론트엔드에 넣으면 안 됩니다.
- 학생에게 공개해도 되는 Supabase Publishable/anon 키만 사용합니다.
- Python 백엔드 코드는 이 프론트엔드 저장소에 넣지 않고 별도 저장소로 관리하는 것을 권장합니다.
