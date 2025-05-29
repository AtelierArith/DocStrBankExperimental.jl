```
GPT3GenerativeFunction(;
    model = "davinci-002",
    temperature = 1.0,
    max_tokens = 1024,
    stop = nothing,
    encoding = GenGPT3.MODEL_ENCODINGS[model],
    api_key_lookup = () -> ENV["OPENAI_API_KEY"],
    organization_lookup = () -> ENV["OPENAI_ORGANIZATION"]
)
```

GPT-3を生成関数として構築し、完了のサンプリングとスコアリングはOpenAI APIへの呼び出しを介して行われます。

生成関数は、プロンプトを（オプションの）引数として受け取り、サンプリングして完了を返します。これは、`max_tokens`の長さまでの文字列の分布を表し、`stop`シーケンスで終了します。完了は、結果のトレースの`output`アドレスに保存されます。

# 引数

  * `model::String`:   クエリする事前学習済みモデル。デフォルトは`"davinci-002"`です。
  * `temperature::Float64 = 1.0`:   ソフトマックス温度。`0.0`と`2.0`の間の値が許可されます。   高い温度はランダム性を増加させます。これが`1.0`に設定されていない場合、   結果の対数確率は正規化されなくなります。
  * `max_tokens::Int = 1024`:   生成される出力トークンの最大数（停止シーケンスを含む）。
  * `encoding::String = GenGPT3.MODEL_ENCODINGS[model]`:   モデルのトークナイザーエンコーディング。ほとんどのモデルでは、これは`"cl100k_base"`です。
  * `stop::Union{String,Nothing} = nothing`:   文字列としての停止シーケンス。指定されていない場合は、デフォルトで`<|endoftext|>`トークンになります。指定された場合、モデルは複数の終了可能性を避けるために、   `<|endoftext|>`トークンを生成することができなくなります。
  * `api_key_lookup::Function`:   使用するOpenAI APIキーを返すゼロ引数関数。デフォルトは、   `"OPENAI_API_KEY"`環境変数を参照します。
  * `organization_lookup::Function`:   使用するOpenAI組織IDを返すゼロ引数関数。   指定されている場合は、デフォルトで`"OPENAI_ORGANIZATION"`環境変数を参照します。
