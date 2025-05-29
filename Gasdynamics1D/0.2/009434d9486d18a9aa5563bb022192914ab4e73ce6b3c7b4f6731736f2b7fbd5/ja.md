```
MachNumber(ρ_over_ρ0::DensityRatio,Isentropic[;gas=Air])
```

密度と停滞密度の比 `ρ_over_ρ0` に対応するマッハ数を計算します。

$$
M = \left( \dfrac{2}{\gamma-1}\left(\dfrac{1}{(\rho/\rho_0)^{(\gamma-1)}} - 1 \right)\right)^{1/2}
$$

引数として `ρ` と `ρ0` を別々に指定することもできます。 `MachNumber(ρ,ρ0)`
