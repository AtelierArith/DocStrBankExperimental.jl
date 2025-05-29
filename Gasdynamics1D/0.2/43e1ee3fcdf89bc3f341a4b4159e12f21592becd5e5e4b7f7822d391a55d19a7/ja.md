```
PressureRatio(M1::MachNumber,NormalShock[;gas=Air])
```

正規衝撃の前後の圧力比を返します。衝撃前のマッハ数 `M1` を用いて、次の式を使用します。

$$
\dfrac{p_2}{p_1} = 1 + 2\dfrac{\gamma}{\gamma+1}(M_1^2-1)
$$
