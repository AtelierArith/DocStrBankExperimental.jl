```
approx_log_evidence(approx::<Approximation>, lfx::LatentFiniteGP, ys)
```

与えられた`approx`imationに基づいて周辺尤度（「証拠」とも呼ばれる）の対数の近似を計算します。`approx_log_evidence`の戻り値は、`lfx`のハイパーパラメータを最適化するために使用できます。
