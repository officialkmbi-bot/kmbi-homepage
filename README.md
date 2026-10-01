# 사단법인 소상공인연구원 홈페이지

사단법인 소상공인연구원(Korea Micro Business Institute)의 공식 홈페이지 소스입니다.
서버 프로그램이나 데이터베이스 없이 **파일만으로 동작하는 정적 사이트**라서, 이 폴더만 있으면 누구든 이어서 관리할 수 있습니다.

- 공개 주소: https://officialkmbi-bot.github.io/kmbi-homepage/
- 소스 저장소: https://github.com/officialkmbi-bot/kmbi-homepage
- 관리 계정: GitHub 아이디 `officialkmbi-bot` (연구원 공용 메일 official.kmbi@gmail.com 으로 가입)
- 최초 제작: 2026년 10월

> 이 홈페이지는 공익법인 지정 요건(기부금 모금액·활용실적 공개, 공익위반 제보기관 홈페이지 연결)을 충족하기 위한 것입니다. 매년 공시 내용을 갱신해 주세요.

---

## 1. 폴더 구성

| 경로 | 내용 | 평소에 고칠 일 |
|---|---|---|
| `index.html` | 홈페이지 본체(디자인·메뉴·연구보고서 목록·연혁·공시 표) | 1년에 몇 번 |
| `board-data.js` | 게시판 글 목록, 연구원 기본정보(전화·이메일·주소) | **자주** |
| `files/` | 게시판 첨부파일(PDF·한글 등) | **자주** |
| `img/news/` | 게시판 행사 사진 | 가끔 |
| `img/reports/` | 연구보고서 표지 | 가끔 |
| `img/org/` | 하단 기관 로고(국세청·국민권익위·중기부) — 지우지 마세요 | 없음 |
| `fonts/` | 글꼴(Pretendard) — 지우지 마세요 | 없음 |
| `.nojekyll` | GitHub Pages용 설정 파일 — 지우지 마세요 | 없음 |

---

## 2. 게시판에 글 올리기 (가장 자주 하는 일)

GitHub 웹사이트에서 바로 할 수 있습니다. 프로그램 설치가 필요 없습니다.

1. **첨부파일 올리기**: 저장소에서 `files` 폴더 → `Add file` → `Upload files` → 파일 끌어놓기 → `Commit changes`
   - 파일명은 영문·숫자로 짧게 하세요. 예) `2026_donation.pdf`
2. **글 추가**: `board-data.js` 열기 → 연필 아이콘(Edit) → `window.POSTS = [` 바로 아래에 기존 글 하나를 복사해 붙이고 고치기

   ```js
   {
     id: 9,                         // 가장 큰 번호 + 1
     cat: "공시자료",                // 공지사항 / 공시자료 / 연구원 동향
     title: "2026년도 기부금 모금액 및 활용실적 공개",
     date: "2027.03.31",
     files: [{ name: "화면에 보일 파일 이름.pdf", path: "files/2026_donation.pdf" }],
     images: [],                    // 사진: ["img/news/사진.jpg"]
     body: "본문 내용"
   },
   ```
   - 큰따옴표(`"`)와 쉼표(`,`)를 지우지 않도록 주의하세요. 하나라도 빠지면 게시판 전체가 안 보입니다.
3. `Commit changes` 누르기 → **1~2분 뒤 홈페이지에 자동 반영**됩니다.
4. 실수했으면: 저장소의 `History`에서 이전 버전으로 되돌릴 수 있습니다.

---

## 3. 매년 해야 할 일 (공익법인 의무)

| 시기 | 할 일 | 고칠 곳 |
|---|---|---|
| 매년 3~4월 (사업연도 종료 후 4개월 이내) | 전년도 **기부금 모금액 및 활용실적** 공개 | `board-data.js`에 공시자료 글 추가 + `index.html`의 「기부금 모금액 및 활용실적」 표에 한 줄 추가 |
| 국세청 결산공시 후 | **결산서류 공시** 내용 반영 | `index.html`의 「결산서류 공시」 표와 메인 화면 「결산 및 기부금 현황」 표에 한 줄 추가, 공시서식 PDF를 `files/`에 올리고 공시자료 글 작성 |
| 연구·행사 후 | 연구보고서 표지·연혁 추가 | `img/reports/`에 표지 올리고 `index.html`의 `REPORTS` 목록과 `HISTORY` 목록에 추가 |

`index.html`에서 고칠 곳은 `Ctrl+F`로 아래 글자를 찾으면 됩니다.
- 기부금 표: `<tr><td>2025</td>`
- 결산 표: `18,206,275`
- 메인 화면 표: `결산 및 기부금 현황`
- 보고서 목록: `const REPORTS`
- 연혁: `const HISTORY`

---

## 4. 처음 인터넷에 올리는 방법 (GitHub Pages, 무료)

1. https://github.com 에서 **연구원 공용 메일(official.kmbi@gmail.com)** 로 계정을 만듭니다. (개인 메일 X — 퇴사해도 연구원이 계속 관리할 수 있게)
2. 오른쪽 위 `+` → `New repository` → 이름 `kmbi-homepage` → **Public** 선택 → `Create repository`
3. `uploading an existing file` 링크 클릭 → 이 폴더 **안의 내용 전체**(index.html, board-data.js, files, img, fonts, .nojekyll 등)를 끌어놓기 → `Commit changes`
   - `.nojekyll`처럼 점으로 시작하는 파일이 윈도우 탐색기에서 안 보이면 `보기 → 숨긴 항목` 체크
4. 저장소 `Settings` → 왼쪽 `Pages` → Source: `Deploy from a branch`, Branch: `main` / `/(root)` → `Save`
5. 1~2분 뒤 같은 화면 위쪽에 주소(`https://계정이름.github.io/kmbi-homepage/`)가 표시됩니다. 이 주소를
   - 공익법인 추천신청서 「홈페이지 주소」 칸
   - 국세청 결산공시 「홈페이지 주소」 칸
   - 이 README 맨 위
   에 적습니다.

### 연구원 도메인을 쓰고 싶을 때 (선택)
도메인(예: `○○.or.kr`)을 구입했다면 `Settings → Pages → Custom domain`에 입력하고, 도메인 업체 관리화면에서 GitHub 안내대로 DNS를 설정하면 됩니다. 도메인 업체 계정도 반드시 연구원 공용 메일로 만드세요.

---

## 5. 인수인계 체크리스트

- [ ] GitHub 계정 아이디·비밀번호를 연구원 내부 보안 문서에 보관 (2단계 인증 복구코드 포함)
- [ ] 후임자 개인 GitHub 계정이 있다면 저장소 `Settings → Collaborators`에 추가 (공용 계정 비밀번호를 돌려쓰지 않아도 됨)
- [ ] 도메인을 쓴다면 도메인 만료일·결제수단 확인
- [ ] 이 README의 공개 주소 칸 최신화
