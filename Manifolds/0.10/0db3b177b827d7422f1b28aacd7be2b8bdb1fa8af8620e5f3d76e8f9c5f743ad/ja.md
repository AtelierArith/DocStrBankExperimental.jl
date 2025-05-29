```
Random.rand(M::Circle{ℝ}; vector_at = nothing, σ::Real=1.0)
```

`vector_at`が`nothing`の場合、$[-\pi,\pi)$から一様にランダムな要素を選んで、[`Circle`](@ref) $\mathbb S^1$上のランダムな点を返します。

`vector_at`が`nothing`でない場合、[`Circle`](@ref)上の点`vector_at`の接空間から、平均0、標準偏差`σ`の正規分布を使用してランダムな接ベクトルを返します。
