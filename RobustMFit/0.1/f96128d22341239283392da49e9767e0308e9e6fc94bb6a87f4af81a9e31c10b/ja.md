```
FInfo(d::UnivariateDistribution)
```

分布 `d` のフィッシャー情報行列。

一般的に使用される分布に対してハードコーディングされています。閉じた形が知られていない場合、関数は勾配と期待値の数値計算に基づいています。

# 例

```julia
d = Poisson(10)
FInfo(d)

d = Normal(0, 1)
FInfo(d)
```

関連情報は [`RAE`](@ref RAE) を参照してください。
