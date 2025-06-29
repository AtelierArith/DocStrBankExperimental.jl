```
estimate_gpd_parameters(X::AbstractVector{<:Real}, estimator::Symbol)
```

`X`にフィットした一般化パレート分布のパラメータ`σ, ξ`を推定して返します（通常は状態空間集合の対数距離の超過値です）、`minimum(X) ≥ 0`であると仮定し、したがってパラメータ`μ`は0です（そうでない場合は、単に`X`をその最小値だけシフトします）。これは[Pons2023](@cite)で提供されている方法に従います。

推定器は次のいずれかです：

  * `:exp`: 分布がGPではなく指数分布であると仮定し、`X`の平均から`σ`を取得し、`ξ = 0`に設定します。
  * `mm`: "モーメント法"を表し、推定値は次のように与えられます。

    $$
    \xi = (\bar{x}^2/s^2 - 1)/2, \quad \sigma = \bar{x}(\bar{x}^2/s^2 + 1)/2
    $$

    ここで、$\bar{x}$はサンプル平均、$s^2$はサンプル分散です。この推定器は、真の分布の`ξ`値が< 0.5である場合にのみ存在します。

```
