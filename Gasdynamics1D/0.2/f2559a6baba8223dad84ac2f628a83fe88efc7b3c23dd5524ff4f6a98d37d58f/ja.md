```
StagnationPressureRatio(M1::MachNumber,NormalShock[;gas=Air])
```

正規衝撃の前後の停滞圧力比を返します。衝撃前のマッハ数 `M1` を用いて、次の式を使用します。

$$
\dfrac{p_{02}}{p_{01}} = \left(\dfrac{(\gamma+1)M_1^2}{2+(\gamma-1)M_1^2}\right)^{\gamma/(\gamma-1)} \left(\dfrac{\gamma+1}{2\gamma M_1^2 - (\gamma-1)}\right)^{1/(\gamma-1)}
$$
