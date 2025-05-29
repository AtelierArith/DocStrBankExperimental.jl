```
DensityDiffusion
```

すべての密度拡散定式の抽象スーパタイプです。

現在、以下の定式が利用可能です：

| 定式                                          | 定常状態シミュレーションに適している | 低計算コスト |
|:------------------------------------------- |:------------------ |:------ |
| [`DensityDiffusionMolteniColagrossi`](@ref) | ❌                  | ✅      |
| [`DensityDiffusionFerrari`](@ref)           | ❌                  | ✅      |
| [`DensityDiffusionAntuono`](@ref)           | ✅                  | ❌      |

比較と詳細については[Density Diffusion](@ref density_diffusion)を参照してください。
