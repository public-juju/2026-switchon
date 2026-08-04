# 2026 스위치온

4주 식단 & 인바디 기록 PWA. 정적 파일만으로 동작해서 별도 빌드 과정이 없어요.

## GitHub에 올리기

1. 새 저장소 생성 (Public, README 없이 또는 있어도 무방)
2. 저장소 화면에서 "uploading an existing file" 클릭
3. 이 폴더 안의 파일 전체(12개, 폴더 없이 전부 한 층)를 한 번에 선택해서 업로드
4. Commit changes

## Vercel로 배포하기

1. https://vercel.com 에 GitHub 계정으로 로그인
2. "Add New... → Project" 클릭
3. 방금 만든 저장소 선택 (Import)
4. Framework Preset은 **Other**로 두기 (빌드 명령 없이 정적 파일 그대로 배포)
   - Build Command: 비워두기
   - Output Directory: 비워두기 (루트 그대로)
5. Deploy 클릭 → 몇 초 뒤 배포 주소가 생겨요

이후로는 GitHub에 push(또는 파일 수정 Commit)할 때마다 Vercel이 자동으로 재배포해줘요.

## 휴대폰에 앱처럼 설치하기 (PWA)

- **iOS(Safari)**: 배포된 주소 접속 → 공유 버튼 → "홈 화면에 추가"
- **Android(Chrome)**: 배포된 주소 접속 → 메뉴(⋮) → "홈 화면에 추가" 또는 자동으로 뜨는 설치 배너 사용

설치하면 주소창 없이 일반 앱처럼 아이콘으로 실행되고, 한 번 접속한 뒤에는 오프라인에서도 앱 화면이 열려요(기록 데이터는 그대로 기기에 저장돼요).

## 파일 구성

모든 파일이 폴더 없이 한 층에 있어요 (휴대폰에서 GitHub에 올리기 쉽게 하기 위함).

```
index.html               앱 본체
manifest.json             PWA 설정 (앱 이름, 아이콘, 테마 색상)
sw.js                      서비스워커 (오프라인 캐싱)
icon-192.png / icon-512.png / icon-maskable-192.png / icon-maskable-512.png / apple-touch-icon.png / favicon-16.png / favicon-32.png
                           앱 아이콘
vercel.json                캐시 헤더 설정
```

## 참고

- 인바디 사진 자동 인식(OCR)은 Tesseract.js를 CDN에서 불러와요. 인터넷이 연결되어 있어야 최초 1회 로드돼요.
- 기록 데이터는 이 브라우저(기기)에만 저장돼요. 다른 기기·다른 브라우저에서는 보이지 않으니, 중요한 기록은 가끔 캡처해서 백업해두는 걸 추천해요.
