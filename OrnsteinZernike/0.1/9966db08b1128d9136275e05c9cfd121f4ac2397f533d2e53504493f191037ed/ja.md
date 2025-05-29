```
VompeMartynov <: Closure
```

Vompe-Martynov閉包を実装します $b(r) = \sqrt{1+2\gamma^*(r) } - \gamma^*(r) - 1 $ 。ここで $\gamma^* = \gamma - u_{LR}$ であり、$ u_{LR}$ はポテンシャルの長距離テールで、$\alpha$ は熱力学的一貫性によって決定できる自由パラメータです。

例:

```julia
closure = VompeMartynov()
```

参考文献:

Vompe, A. G., and G. A. Martynov. "The bridge function expansion and the self‐consistency problem of the Ornstein–Zernike equation solution." The Journal of chemical physics 100.7 (1994): 5249-5258.
