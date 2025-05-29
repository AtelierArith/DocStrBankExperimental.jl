```
conformal_model(model::Supervised; method::Union{Nothing, Symbol}=nothing, kwargs...)
```

`model::Supervised` を適合モデルに変換するシンプルなラッパー関数です。適合予測のための希望する `method` を指定するために使用できるオプションのキーワード引数と、`method` に特有の追加の `kwargs...` を受け入れます。
