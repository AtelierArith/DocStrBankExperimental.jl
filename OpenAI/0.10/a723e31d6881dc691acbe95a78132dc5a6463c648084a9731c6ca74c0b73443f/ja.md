# 引数:

  * `api_key::String`: OpenAI APIキー
  * `model_id::String`: モデルID

# キーワード引数（詳細なリストについてはOpenAIのドキュメントを確認してください）:

  * `temperature::Float64=1.0`: 使用するサンプリング温度で、0から2の間の値です。0.8のような高い値は出力をよりランダムにし、0.2のような低い値はより焦点を絞り、決定的にします。一般的には、これまたはtop_pを変更することをお勧めしますが、両方は変更しないでください。
  * `top_p::Float64=1.0`: 温度を使ったサンプリングの代替手法で、核サンプリングと呼ばれ、モデルはtop_p確率質量を持つトークンの結果を考慮します。したがって、0.1は上位10%の確率質量を構成するトークンのみが考慮されることを意味します。一般的には、これまたはtemperatureを変更することをお勧めしますが、両方は変更しないでください。

エンドポイントや追加の引数についての詳細は、[https://platform.openai.com/docs/api-reference/completions](https://platform.openai.com/docs/api-reference/completions)を訪れてください。

# HTTP.requestキーワード引数:

  * `http_kwargs::NamedTuple=NamedTuple()`: HTTP.requestに渡すキーワード引数（例: `http_kwargs=(connection_timeout=2,)`は接続タイムアウトを2秒に設定します）。
