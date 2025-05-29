```
MvNormalMeanPrecision{T <: Real, M <: AbstractVector{T}, P <: AbstractMatrix{T}} <: AbstractMvNormal
```

平均 `μ` と精度行列 `Λ` を持つ多変量正規分布であり、`T` はベクトル `M` と行列 `P` の要素型です。

# フィールド

  * `μ::M`: 多変量正規分布の平均ベクトル。
  * `Λ::P`: 多変量正規分布の精度行列（共分散行列の逆）。
