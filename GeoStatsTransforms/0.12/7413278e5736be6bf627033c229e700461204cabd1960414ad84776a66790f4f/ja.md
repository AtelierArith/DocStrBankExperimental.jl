```
Aggregate(domain, var₁ => agg₁, var₂ => agg₂, ..., varₙ => aggₙ)
Aggregate([g₁, g₂, ..., gₙ], var₁ => agg₁, var₂ => agg₂, ..., varₙ => aggₙ)
```

ジオスペーシャル `domain` 上で変数 `var₁`, `var₂`, ..., `varₙ` を集約関数 `agg₁`, `agg₂`, ..., `aggₙ` を使用して集約します。あるいは、幾何学的な `g₁`, `g₂`, ..., `gₙ` 上で変数を集約します。デフォルトの集約関数は連続変数に対しては `mean` であり、それ以外の場合は `first` です。

# 例

```julia
Aggregate(domain, 1 => last, 2 => maximum)
Aggregate(domain, :a => first, :b => minimum)
Aggregate(domain, "a" => last, "b" => maximum)
Aggregate(geoms, "a" => last, "b" => maximum)
```
