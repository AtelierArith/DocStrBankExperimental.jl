```
BomontBretonnet <: Closure
```

ボモン・ブレトネット閉包 $b(r) = \sqrt{1+2\gamma^*(r) + f \gamma^*(r)^2} - \gamma^*(r) - 1 $ を実装します。ここで $\gamma^* = \gamma - u_{LR}$ であり、$u_{LR}$ はポテンシャルの長距離テール、$f$ は熱力学的一貫性に基づいて決定できる自由パラメータです。

例:

```julia
closure = BomontBretonnet(0.5)
```

参考文献:

Bomont, J. M., and J. L. Bretonnet. "A self-consistent integral equation: Bridge function and thermodynamic properties for the Lennard-Jones fluid." The Journal of chemical physics 119.4 (2003): 2188-2191.
