```
ScalableASM(u, λ, Δx, Δy, z; expand=true)
```

自動的にスケーラブルASMによってスケーリングされた回折場を返します（参照 1）。目的平面におけるサンプリングピッチ $\Delta_{d}$ は $\Delta_{d}=\dfrac{\lambda z}{pN\Delta_{s}}$ であり、ここで $\Delta_{s}$ はソース平面におけるサンプリングピッチ、$N$ はソースまたは目的平面のピクセル数、$p=2$ はパディングファクターです。

> 1. [Rainer Heintzmann, Lars Loetgering, and Felix Wechsler, "Scalable angular spectrum propagation," Optica **10**, 1407-1416 (2023)](https://doi.org/10.1364/OPTICA.497809)

