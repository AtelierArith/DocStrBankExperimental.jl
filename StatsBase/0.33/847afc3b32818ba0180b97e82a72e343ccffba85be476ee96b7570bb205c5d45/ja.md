```
mean!(R::AbstractArray, A::AbstractArray, w::AbstractWeights[; dims=nothing])
```

配列 `A` の重みベクトル `w`（型 `AbstractWeights`）を用いて、次元 `dims` に沿った加重平均を計算し、結果を `R` に書き込みます。
