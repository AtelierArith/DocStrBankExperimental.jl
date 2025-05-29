```
EqualVarianceTTest(nx::Int, ny::Int, mx::Real, my::Real, vx::Real, vy::Real, μ0::Real=0)
```

サンプル `x` と `y` が要素数 `nx` と `ny`、平均 `mx` と `my`、分散 `vx` と `vy` で記述されるという帰無仮説の二標本t検定を実行します。対立仮説は、分布が異なる平均を持つが等しい分散を持つというものです。

実装: [`pvalue`](@ref), [`confint`](@ref)
