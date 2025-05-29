```
Google LLM
```

Google LLM APIにアクセスするためのパラメータをカプセル化する構造。

  * `api_key`: Google Gemini APIにアクセスするためのAPIキー（`https://ai.google.dev/gemini-api/docs/`）で、環境変数`GOOGLE_API_KEY`から読み取ります。
  * `model_id`: クエリするモデルの文字列識別子。利用可能なモデルのリストについては`https://ai.google.dev/gemini-api/docs/models/gemini`を参照してください。
  * `url`: チャット完了のためのURL。デフォルトは`https://generativelanguage.googleapis.com/v1beta/models/{{model_id}}`です。
