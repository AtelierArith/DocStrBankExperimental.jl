```
approx_lml(approx::<Approximation>, lfx::LatentFiniteGP, ys)
```

与えられた `approx` に基づいて、周辺尤度の対数（「証拠」とも呼ばれる）の近似を計算します。この近似は、`lfx` のハイパーパラメータを最適化するために使用できます。

これは AbstractGPs API の一部となるべきです（JuliaGaussianProcesses/AbstractGPs.jl#221）。
