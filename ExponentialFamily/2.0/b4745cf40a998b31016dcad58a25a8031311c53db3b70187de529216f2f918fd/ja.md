```
MvNormalMeanCovariance{T <: Real, M <: AbstractVector{T}, P <: AbstractMatrix{T}} <: AbstractMvNormal
```

平均 `μ` と共分散行列 `Σ` を持つ多変量正規分布であり、`T` はベクトル `M` と行列 `P` の要素型です。

# フィールド

  * `μ::M`: 多変量正規分布の平均ベクトル。
  * `Σ::P`: 多変量正規分布の共分散行列。
