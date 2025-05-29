画像を作成する

# 引数:

  * `api_key::String`: OpenAI APIキー
  * `prompt`: 画像を生成するための入力テキスト。Stringまたはトークンの配列。
  * `n::Integer`: オプション。生成する画像の数。1から10の間でなければならない。
  * `size::String`: オプション。デフォルトは1024x1024。生成される画像のサイズ。256x256、512x512、または1024x1024のいずれかでなければならない。

# キーワード引数:

  * `http_kwargs::NamedTuple`: オプション。HTTP.requestに渡すキーワード引数。
  * `response_format::String`: オプション。デフォルトは "url"。レスポンスの形式。"url" または "b64_json" のいずれかでなければならない。

エンドポイントの詳細については、[https://platform.openai.com/docs/api-reference/images/create](https://platform.openai.com/docs/api-reference/images/create)を訪問してください。

# リクエストが行われたら、

このようにダウンロードします: `download(r.response["data"][begin]["url"], "image.png")`
