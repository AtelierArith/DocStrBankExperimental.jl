```
ksmin_adaptive(x, hardness=50; tol=1e-6, smoothing_fraction=0.1)
```

Kreisselmeier–Steinhauser制約集約関数で、PoonとMartinsによって提案された適応的な硬度を使用しています。「隣接感度分析を用いた制約集約への適応的アプローチ」において。この実装では、硬度値を増加させるためにセカント法ではなくニュートン法を使用しています。また、結果がC1連続であることを保証するために、いくつかのブレンドも使用されています。`smoothing_fraction`は、このブレンドの滑らかさを制御します。
