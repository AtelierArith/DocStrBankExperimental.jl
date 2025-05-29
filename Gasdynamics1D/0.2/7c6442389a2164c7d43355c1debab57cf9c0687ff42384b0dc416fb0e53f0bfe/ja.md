```
MachNumber(M1::MachNumber,NormalShock[;gas=Air])
```

衝撃前のマッハ数 `M1` を用いて、ノーマルショック後のマッハ数を返します。使用する方程式は次の通りです。

$$
M_2^2 = \dfrac{2 + (\gamma-1)M_1^2}{2\gamma M_1^2 - (\gamma-1)}
$$
