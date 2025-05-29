```
GPT3Mixture(;
    model = "davinci-002",
    temperature = 1.0,
    max_tokens = 1024,
    stop = nothing,
    batch_size = 10,
    encoding = GenGPT3.MODEL_ENCODINGS[model],
    api_key_lookup = () -> ENV["OPENAI_API_KEY"],
    organization_lookup = () -> ENV["OPENAI_ORGANIZATION"]
)
```

異なるプロンプトを持つ [`GPT3GenerativeFunction`](@ref) の混合。プロンプトのベクトルと確率のベクトルを受け取り、確率に従って混合からサンプリングします。確率引数が省略された場合、混合はプロンプトに対して均一になります。

これは、最初にプロンプトに対するカテゴリカル分布からサンプリングし、次に選択されたプロンプトに対する補完をサンプリングする `@gen` 関数を書くことと同等です。しかし、内部で [`MultiGPT3GF`](@ref) を使用してバッチAPI呼び出しを行うことで、より効率的に動作します。
