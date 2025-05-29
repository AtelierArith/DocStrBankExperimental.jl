```
ksmax_adaptive(x, hardness=50; tol=1e-6, smoothing_fraction=0.1)
```

Kreisselmeier–Steinhauser 制約集約関数で、Poon と Martins によって提案された適応的な硬度を使用しています。「隣接感度分析を用いた制約集約への適応的アプローチ」において。この実装では、硬度値を増加させるためにセカント法ではなくニュートン法を使用しています。また、結果が C1 連続であることを保証するために、いくつかのブレンドも使用されています。`smoothing_fraction` はこのブレンドの滑らかさを制御します。
