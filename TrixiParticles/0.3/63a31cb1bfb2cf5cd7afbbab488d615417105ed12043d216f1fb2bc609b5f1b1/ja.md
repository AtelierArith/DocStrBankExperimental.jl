```
MixedKernelGradientCorrection()
```

[`GradientCorrection`](@ref) と [`KernelCorrection`](@ref) を組み合わせたもので、1次精度のSPH手法を実現します（[Bonet, 1999](@cite Bonet1999)を参照）。

# 注意事項:

  * 特に粒子が小さなクラスターに分離する際の安定性の問題。
  * 計算コストが2倍になります。
