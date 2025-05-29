```
ρOverρStar(M::MachNumber,FannoFlow[;gas=PerfectGas]) -> DensityRatio
```

ファノ流における密度と音速密度の比を、マッハ数 `M` から計算します。

$$
\dfrac{\rho}{\rho^*} = \dfrac{1}{M} \left(\dfrac{2+(\gamma-1)M^2}{\gamma+1}\right)^{1/2}
$$
