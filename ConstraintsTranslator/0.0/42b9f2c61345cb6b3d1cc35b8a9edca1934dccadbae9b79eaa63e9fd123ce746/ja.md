```
GroqLLM
```

Groq LLM APIにアクセスするためのパラメータをカプセル化する構造体。

  * `api_key`: Groq API (https://groq.com) にアクセスするためのAPIキーで、環境変数GROQ*API*KEYから読み取られます。
  * `model_id`: クエリするモデルの文字列識別子。利用可能なモデルのリストについては https://console.groq.com/docs/models を参照してください。
  * `url`: チャット完了のためのURL。デフォルトは "https://api.groq.com/openai/v1/chat/completions" です。
