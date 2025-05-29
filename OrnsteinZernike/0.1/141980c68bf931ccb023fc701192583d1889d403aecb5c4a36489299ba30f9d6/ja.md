```
ChoudhuryGhosh <: Closure
```

Choudhury-Ghosh閉包を実装します $b(r) = -\frac{-\gamma^*(r)^2}{2(1+\alpha \gamma^*(r))} $ ただし $\gamma^*(r) >0$ の場合、そうでなければ $b(r)=-\gamma^*(r)^2/2$ です。ここで $\gamma^* = \gamma - u_{LR}$ であり、$ u_{LR}$ はポテンシャルの長距離尾で、$\alpha$ は経験的関係によって決定される自由パラメータです。

例:

```julia
α(ρ) = 1.01752 - 0.275ρ # この経験的関係については参考文献を参照してください
closure = ChoudhuryGhosh(α(0.4))
```

参考文献:

Choudhury, Niharendu, and Swapan K. Ghosh. "Integral equation theory of Lennard-Jones fluids: A modified Verlet bridge function approach." The Journal of chemical physics 116.19 (2002): 8517-8522.
