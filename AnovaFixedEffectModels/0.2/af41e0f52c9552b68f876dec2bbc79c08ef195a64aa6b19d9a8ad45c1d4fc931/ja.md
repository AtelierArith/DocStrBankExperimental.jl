```
nestedmodels(modeltype::Type{FixedEffectModel}, f::FormulaTerm, data; null = true, kwargs...)
```

モデルタイプ、フォーミュラ、データからネストされたモデルを生成します。キーワード引数 null が true の場合（デフォルト）、null モデルは空のモデルになります。
