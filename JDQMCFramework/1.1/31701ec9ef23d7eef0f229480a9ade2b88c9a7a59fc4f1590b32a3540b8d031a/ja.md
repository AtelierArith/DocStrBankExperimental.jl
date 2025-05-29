```
abstract type AbstractPropagator{T<:Continuous, E<:Continuous} end
```

抽象型は、虚時間伝播子行列 $B$ を表します。すべての特定の伝播子型は、この抽象型を継承します。上記の `T` は、行列要素のデータ型であり、指数化された運動エネルギー行列 $e^{-\Delta\tau K_l}$ に現れるもので、`E` は、対角の指数化されたポテンシャルエネルギー行列 $e^{-\Delta\tau V_l}$ に現れる行列要素のデータ型です。
