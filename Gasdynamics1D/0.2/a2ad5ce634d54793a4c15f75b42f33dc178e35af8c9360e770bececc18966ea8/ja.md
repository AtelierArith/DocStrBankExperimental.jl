```
StagnationDensity(ρ::Density,M::MachNumber,Isentropic[;gas=Air])
```

密度 `ρ` とマッハ数 `M` に対応する停滞密度を計算します。

$$
\rho_0 = \rho \left( 1 + \dfrac{\gamma-1}{2} M^2\right)^{1/(\gamma-1)}
$$
