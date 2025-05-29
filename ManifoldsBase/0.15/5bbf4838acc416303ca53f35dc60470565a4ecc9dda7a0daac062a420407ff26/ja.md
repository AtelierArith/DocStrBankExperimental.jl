```
norm(M::AbstractPowerManifold, p, X, r::Real=2)
```

`M`上の[`AbstractPowerManifold`](@ref)における点`p`の接空間からの`X`のノルムを計算します。すなわち、要素ごとのノルム`r`-ノルムが計算され、デフォルトの`r=2`はフロベニウスノルムが計算されます。
