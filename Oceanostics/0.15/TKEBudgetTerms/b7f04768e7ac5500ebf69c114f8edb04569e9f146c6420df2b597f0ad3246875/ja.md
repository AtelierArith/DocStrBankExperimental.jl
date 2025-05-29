```julia
KineticEnergyForcingTerm(model; location)

```

KE予測方程の強制項を計算する`KernelFunctionOperation`を返します：

```
    FORC = uᵢFᵤᵢ
```

ここで、`uᵢ`は速度成分であり、`Fᵤᵢ`は`uᵢ`予測方程における強制項です（すなわち、`uᵢ`のための強制）。
