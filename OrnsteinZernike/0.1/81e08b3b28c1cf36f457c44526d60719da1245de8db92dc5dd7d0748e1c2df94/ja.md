ZerahHansen <: Closure

Zerah-Hansen (HMSA) (HNC-SMSA) クローズ $b(r) = \ln(\frac{\exp(f(r)\gamma^*(r)) - 1}{f(r)} + 1) - γ^*(r) $ を実装します。ここで $\gamma^* = \gamma - u_{LR}$ であり、$ u_{LR}$ はポテンシャルの長距離テールで、$f(r)=1-\exp(-\alpha r)$ であり、$\alpha$ は自由パラメータで、熱力学的一貫性が達成されるように選択できます。

例:

```julia
closure = ZerahHansen(0.5)
```

参考文献:

Zerah, Gilles, and Jean‐Pierre Hansen. "Self‐consistent integral equations for fluid pair distribution functions: Another attempt." The Journal of chemical physics 84.4 (1986): 2336-2343.
