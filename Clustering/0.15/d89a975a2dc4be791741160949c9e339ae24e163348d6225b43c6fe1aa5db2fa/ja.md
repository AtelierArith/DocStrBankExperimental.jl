```
KmeansResult{C,D<:Real,WC<:Real} <: ClusteringResult
```

[`kmeans`](@ref) と [`kmeans!`](@ref) の出力。

# 型パラメータ

  * `C<:AbstractMatrix{<:AbstractFloat}`: `centers` 行列の型
  * `D<:Real`: 割り当てコストの型
  * `WC<:Real`: クラスタ重みの型
