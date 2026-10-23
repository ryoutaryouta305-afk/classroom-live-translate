# Classroom Live Translate

学校のiPadブラウザで、英語の授業音声を英語文字起こし＋日本語翻訳することを目指した、無料の静的Webアプリです。

## 重要な制約

- APIキー不要、推論用の有料APIを呼び出しません。
- 音声認識・翻訳はブラウザ内で実行する設計です。音声をサーバーへアップロードしたり録音保存したりしません。
- 初回はTransformers.jsと2つのモデルを公開CDN/Hugging Faceから取得します。初回やキャッシュ消去後は通信が必要です。
- 「無制限・常時安定」を保証することはできません。端末のメモリ、CPU/GPU、バッテリー、通信、ブラウザ制限に依存します。
- iPad実機での動作試験が必要です。モデルのロード失敗やメモリ不足の可能性があります。
- 学校の規則と先生の指示に従ってください。

## GitHub Pagesで無料公開する方法

1. GitHubで新しい**Public**リポジトリを作成（例: `classroom-live-translate`）。既存の別プロジェクトには混ぜないでください。
2. `index.html` をリポジトリのルートにアップロードしてコミットします。
3. リポジトリの **Settings → Pages** を開きます。
4. **Build and deployment → Deploy from a branch** を選び、Branch を `main`、folder を `/(root)` にして保存します。
5. 公開URL（通常は `https://USERNAME.github.io/classroom-live-translate/`）が表示されたらiPadで開きます。
6. 最初にモデル読み込みを押し、Wi‑Fiでダウンロードを待ちます。その後、マイク開始を押して許可します。

GitHub Pagesは静的ファイルのホスティングに利用します。公開前にリポジトリがPublicであることと、学校のネットワークでCDN/Hugging Faceへの接続が許可されていることを確認してください。

## 動作確認手順

1. HTTPSのURLで開く。
2. モデル読み込みが完了するまで待つ（初回は長くかかる場合があります）。
3. マイクを許可し、静かな場所で英語を10〜20秒試す。
4. 英語と日本語の両方が表示されるか確認。
5. 失敗時はページを再読み込みし、ネットワーク制限・空き容量・ブラウザのマイク権限を確認。

## 技術

- Transformers.js 3.7.2
- ASR: `onnx-community/whisper-tiny.en`
- Translation: `Xenova/opus-mt-en-jap`
- `getUserMedia` + Web Audio API
- 静的HTML/CSS/JavaScript。サーバー、APIキー、課金アカウントは不要。
