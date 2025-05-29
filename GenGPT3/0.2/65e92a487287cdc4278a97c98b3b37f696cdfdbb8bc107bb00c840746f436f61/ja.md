```
MultiGPT3GenerativeFunction(;
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

[`GPT3GenerativeFunction`](@ref)のバッチ版で、バッチのプロンプトに対して完了をリクエストし、返します。引数として`String`型のプロンプトの`Vector`を受け取ります。`i`番目のプロンプトの完了は、結果のトレースの`i => output`アドレスに格納されます。
