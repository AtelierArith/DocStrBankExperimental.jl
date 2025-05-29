```
DensityRatio(M1::MachNumber,NormalShock[;gas=Air])
```

正規衝撃の前のマッハ数 `M1` を用いて、衝撃前後の密度の比を返します。式は次の通りです。

$$
\dfrac{\rho_2}{\rho_1} = \dfrac{(\gamma+1)M_1^2}{2+(\gamma-1)M_1^2}
$$
