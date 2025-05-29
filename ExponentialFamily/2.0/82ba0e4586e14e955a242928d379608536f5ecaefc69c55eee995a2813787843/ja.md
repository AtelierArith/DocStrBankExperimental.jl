```
MvNormalWeightedMeanPrecision{T <: Real, M <: AbstractVector{T}, P <: AbstractMatrix{T}} <: AbstractMvNormal
```

重み付き平均ベクトル `xi` と精度行列 `Λ` を持つ多変量正規分布であり、`T` はベクトル `M` と行列 `P` の要素型です。この構造体は多変量ガウス分布の自然なパラメータ化を表します。

# フィールド

  * `xi::M`: 多変量正規分布の重み付き平均ベクトル。
  * `Λ::P`: 多変量正規分布の精度行列（共分散行列の逆）。
