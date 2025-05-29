```
wcounts(R::ClusteringResult) -> Vector{Float64}
wcounts(R::FuzzyCMeansResult) -> Vector{Float64}
```

各クラスタに割り当てられたポイントの重みの合計として、重み付きクラスタサイズを取得します。

非重み付きクラスタリングの場合、すべてのデータポイントの重みは1.0であると仮定されるため、結果は`convert(Vector{Float64}, counts(R))`と同等です。
