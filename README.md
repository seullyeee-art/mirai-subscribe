# MIRAI 구독 안내 페이지 (MAX)

캐릭터 챗 서비스 MIRAI의 **MAX 구독 안내** 페이지. 단일 `index.html` (self-contained — 외부 의존성 없음, 폰트 CDN만).

**라이브:** https://seullyeee-art.github.io/mirai-subscribe/

---

## 실행
- 그냥 `index.html`을 브라우저로 열면 됨 (이미지 상대경로 때문에 `file://`도 동작).
- 로컬 서버: `python3 -m http.server` → `http://localhost:8000/`

## 구조
1. **Hero** — 캐릭터 이미지(저opacity + 그린 글로우) + 헤드라인 `100,000+ 인기 캐릭터`
2. **무료 vs MAX 비교표** — 비인터랙티브, 혜택 강조용. 무료=`✓`/`—`, MAX=그라데이션 `✓`
3. **연간 / 월간 선택 카드** — 클릭 선택, 연간 기본
4. **하단 CTA** — 모바일 고정 바 / 데스크탑 인라인

## 이미지 교체
`images/` 의 두 파일만 사용:
- `hero-ko.webp` — 한국(KR) 히어로 (여성)
- `hero-en.webp` — 글로벌(EN) 히어로 (남성)

→ 같은 파일명으로 **덮어쓰면 끝**. 와이드 배너 권장, 얼굴이 상단에 오게(`background-position: center top`). webp 변환: `cwebp -q 90 in.png -o hero-ko.webp`

## KO/EN 토글 (좌상단 — 개발자 확인용)
- 텍스트: 각 요소의 `data-ko` / `data-en` 속성
- 이미지: `hero-{ko|en}.webp` 자동 전환
- **운영 배포 시** `.lang-toggle` 블록(HTML/CSS)만 지우면 제거됨

## 가격 (확정값)
- 월간 **$39.99** / 연간 **25% 할인 → $30.00/월** (연 총액 $360)
- 정의 위치 2곳, 수정 시 **둘 다** 변경:
  - JS `I18N` 객체 (CTA·토스트 문구)
  - `.opt` 카드 안의 `$30.00` / `$39.99` 하드코딩

## 디자인
- 다크모드, primary = Mojito 그린 `#14C391`. 토큰은 `:root`에 인라인.
- MAX 배지·체크 = **그린→하늘색 그라데이션** (`#maxGrad` SVG def + `.max-badge`)
- 폰트 그라데이션은 **밝은 톤만** (다크 배경 가독성)

## 배포
`git push origin main` → GitHub Pages(`main` / `root`)가 1~2분 후 자동 빌드.
공개 레포라 링크는 **전 세계 공개**임 (미공개 가격/아트 노출 주의 — 검토 후 Pages 끄려면 Settings → Pages → None).

## TODO / 임시값
- 혜택 카피·`+100턴`·`2배` 등 **수치는 임시안** → 실제 MAX 스펙 확정 시 교체
- `subscribe()`는 토스트만 (결제 SDK 미연동)
