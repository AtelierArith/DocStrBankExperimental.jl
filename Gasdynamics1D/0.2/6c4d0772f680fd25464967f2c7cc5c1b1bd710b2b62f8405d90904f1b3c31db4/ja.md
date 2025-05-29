```
TemperatureRatio(M1::MachNumber,NormalShock[;gas=Air])
```

正規衝撃の前のマッハ数 `M1` を用いて、衝撃の前後の温度比を返します。式は次の通りです。

$$
\dfrac{T_2}{T_1} = 1 + 2\dfrac{(\gamma-1)}{(\gamma+1)^2}\dfrac{(1+\gamma M_1^2)(M_1^2-1)}{M_1^2}
$$
