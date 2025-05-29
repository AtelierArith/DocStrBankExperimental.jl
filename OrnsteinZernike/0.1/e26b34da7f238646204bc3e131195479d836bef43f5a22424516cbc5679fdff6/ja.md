```
CharpentierJackse <: Closure
```

Charpentier-Jackse閉包を実装します $b(r) = \frac{1}{2\alpha}\left(\sqrt{1+4\alpha\gamma^*(r) } - 2\alpha\gamma^*(r) - 1\right) $。ここで $\gamma^* = \gamma - u_{LR}$ であり、$ u_{LR}$ はポテンシャルの長距離尾で、$\alpha$ は熱力学的一貫性により決定できる自由パラメータです。

例:

```julia
closure = CharpentierJackse(0.5)
```

参考文献:

Charpentier, I., and N. Jakse. "Exact numerical derivatives of the pair-correlation function of simple liquids using the tangent linear method." The Journal of Chemical Physics 114.5 (2001): 2284-2292.
