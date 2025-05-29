```
approx_lml(la::LaplaceApproximation, lfx::LatentFiniteGP, ys)
```

周辺尤度の対数（「証拠」とも呼ばれる）の近似を計算します。これは、`lfx`のハイパーパラメータを最適化するために使用できます。

これはAbstractGPs APIの一部となるべきです（JuliaGaussianProcesses/AbstractGPs.jl#221を参照）。
