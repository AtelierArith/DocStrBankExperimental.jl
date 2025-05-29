```
SoftCoreMeanSpherical <: Closure
```

ソフトコア平均球閉包を実装します $b(r) = \ln(\gamma^*(r) + 1) - \gamma^*(r)$。ここで $\gamma^* = \gamma - u_{LR}$ であり、$u_{LR}$ はポテンシャルの長距離テールです。

例:

```julia
closure = SoftCoreMeanSpherical()
```

参考文献:
