```
DuhHaymet <: Closure
```

Duh-Haymetクロージャを実装します $b(r) = \frac{-\gamma^*(r)^2}{2\left[1+\left(\frac{5\gamma^*(r)+11}{7\gamma^*(r)+9}\right)\gamma^*(r)\right]} $ ただし $\gamma^*(r) >0$ の場合、そうでない場合は $b(r)=-\gamma^*(r)^2/2$ です。ここで $\gamma^* = \gamma - u_{LR}$ であり、$ u_{LR}$ はポテンシャルの長距離テールです。

例:

```julia
closure = DuhHaymet()
```

参考文献:
