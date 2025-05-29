```
SMC(space...)
SMC([resampler = AdvancedPS.ResampleWithESSThreshold(), space = ()])
SMC([resampler = AdvancedPS.resample_systematic, ]threshold[, space = ()])
```

変数 `space` のための [`SMC`](@ref) タイプの逐次モンテカルロサンプラーを作成します。

再サンプリングステップのアルゴリズムが明示的に指定されていない場合、推定された有効サンプルサイズが粒子ごとに 0.5 未満に低下すると、系統的再サンプリングが実行されます。
