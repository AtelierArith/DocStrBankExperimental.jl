```julia
KineticEnergyStressTerm(model; location)

```

KE予測方程の拡散項を計算する`KernelFunctionOperation`を返します：

```
    DIFF = uᵢ∂ⱼτᵢⱼ
```

ここで`uᵢ`は速度成分であり、`τᵢⱼ`は`j`方向の`i`運動量の拡散フラックスです。
