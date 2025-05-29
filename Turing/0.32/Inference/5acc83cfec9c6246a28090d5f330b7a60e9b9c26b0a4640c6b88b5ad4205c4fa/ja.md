```
PG(n, space...)
PG(n, [resampler = AdvancedPS.ResampleWithESSThreshold(), space = ()])
PG(n, [resampler = AdvancedPS.resample_systematic, ]threshold[, space = ()])
```

`space`の変数に対して`n`個の粒子を持つタイプ[`PG`](@ref)の粒子ギブスサンプラーを作成します。

再サンプリングステップのアルゴリズムが明示的に指定されていない場合、推定された有効サンプルサイズが粒子ごとに0.5未満に低下すると、系統的再サンプリングが実行されます。
