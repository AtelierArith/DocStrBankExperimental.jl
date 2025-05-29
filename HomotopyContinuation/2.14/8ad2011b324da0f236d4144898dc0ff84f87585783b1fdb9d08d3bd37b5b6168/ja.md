```
WeightedNorm(d::AbstractVector, norm::AbstractNorm; options...)
WeightedNorm(norm::AbstractNorm, n::Integer; options...)
WeightedNorm(norm::AbstractNorm, x::AbstractVector; options...)
```

`WeightedNorm`は、`n`次元ベクトル空間のノルム`norm`の重み付きバリアントを表します。ノルム$||x||$は、追加の重みのベクトル`d`を導入することによって重み付けされ、新しいノルムは$||D⁻¹x||$となります。ここで$D$は対角行列で、対角成分は$d$です。`WeightedNorm`は、[`init!(::WeightedNorm, x)`](@ref)および[`update!(::WeightedNorm, x)`](@ref)を使用して重みを動的に変更するように設計されています。重みは$||D⁻¹x|| ≈ 1.0$となるように構成されています。重みはインデックスを使用してアクセスおよび変更できます。

### オプション

  * `scale_min = sqrt(eps())`: `dᵢ`の最小サイズは、`x`の（重み付き）ノルムの`scale_min`倍です。
  * `scale_abs_min = min(scale_min^2, 200 * sqrt(eps()))`: `dᵢ`の絶対最小サイズ。
  * `scale_max = 1.0 / eps() / sqrt(2)`: `dᵢ`の絶対最大サイズ。

```
