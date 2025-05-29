```
log(M::MetricManifold{ℝ,<:Stiefel{<:Any,ℝ},<:StiefelSubmersionMetric}, p, q; kwargs...)
```

[`Stiefel(n,k)`](@ref) 多様体に対して [`StiefelSubmersionMetric`](@ref) に関する対数写像を計算します。

対数写像は [`ShootingInverseRetraction`](@extref `ManifoldsBase.ShootingInverseRetraction`) を使用して計算されます。$k ≤ \lfloor\frac{n}{2}\rfloor$ の場合、[ZimmermannHueper:2022](@cite) の $k$-shooting メソッドを使用して高速化されます。キーワード引数は `ShootingInverseRetraction` に転送されます。詳細についてはそのドキュメントを参照してください。デフォルトは次のとおりです：

  * `num_transport_points=4`
  * `tolerance=sqrt(eps())`
  * `max_iterations=1_000`
