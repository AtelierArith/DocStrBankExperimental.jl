埋め込みを作成する

# 引数:

  * `api_key::String`: OpenAI APIキー
  * `input`: 埋め込みを生成するための入力テキスト。Stringまたはトークンの配列として指定します。単一のリクエストで複数の入力の埋め込みを取得するには、文字列の配列またはトークン配列の配列を渡します。各入力は8192トークンを超えてはいけません。       - `model_id::String`: モデルID。デフォルトはtext-embedding-ada-002です。

    ```
      # キーワード引数:
      - `http_kwargs::NamedTuple`: オプション。HTTP.requestに渡すキーワード引数。

      エンドポイントの詳細については、<https://platform.openai.com/docs/api-reference/embeddings>を参照してください。
    ```
