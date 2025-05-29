```
    ρ0Overρ(M::MachNumber,Isentropic[;gas=PerfectGas]) -> DensityRatio
```

マッハ数 `M` に対する停滞密度と密度の比を計算します。

$$
\dfrac{\rho_0}{\rho} = \left(1 + \dfrac{\gamma-1}{2}M^2 \right)^{1/(\gamma-1)}
$$
