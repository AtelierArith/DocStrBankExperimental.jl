```
uvit_saturation_corr(count_rate[, frames_per_sec=28.717])
```

飽和効果に対してUVITソースカウントレートを補正します。

この関数はTandon et al. (2017)で提供されたアルゴリズムに基づいており、`uvit_aphot.jl`で円形抽出領域のみに使用されます。
