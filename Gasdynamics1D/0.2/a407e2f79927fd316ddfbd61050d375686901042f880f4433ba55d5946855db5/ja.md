```
Density(ρ0::StagnationDensity,M::MachNumber,Isentropic[;gas=Air])
```

停滞密度 `ρ0` とマッハ数 `M` に対応する密度を計算します。

$$
\rho = \rho_0 \left( 1 + \dfrac{\gamma-1}{2} M^2\right)^{-1/(\gamma-1)}
$$
