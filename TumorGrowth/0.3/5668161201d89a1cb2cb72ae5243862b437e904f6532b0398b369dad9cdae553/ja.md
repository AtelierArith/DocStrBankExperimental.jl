```
logistic(times, v0, v∞, ω)
```

指定された `times` に対して、病変成長の古典的ロジスティック（ヴェルフスト）モデルの解析解に基づいて体積を返します。ここで `p` は `v0`、`v∞`、`ω` のプロパティを持ち、`v0` は時間 `times[1]` における体積です。

これは [`bertalanffy`](@ref) モデルの `λ=-1` のケースです。

すべてのモデルのリストについては [`TumorGrowth`](@ref) を参照してください。
