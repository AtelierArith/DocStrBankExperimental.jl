```
LogDensityFunction(
    ldf::LogDensityFunction,
    adtype::Union{Nothing,ADTypes.AbstractADType}
)
```

与えられた `ldf` 引数からモデル、varinfo、およびコンテキストを使用して新しい LogDensityFunction を作成しますが、AD タイプは `adtype` に設定されます。AD タイプを削除するには、2 番目の引数として `nothing` を渡します。
