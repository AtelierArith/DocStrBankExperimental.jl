```
StagnationDensity(T0::StagnationTemperature,p0::StagnationPressure[;gas=Air])
```

停滞密度を停滞温度 `T0` と停滞圧 `p0` から計算します。使用する式は次の通りです。

$$
\rho_0 = p_0/(\rho T_0)
$$

引数の順序を入れ替えることもできます。
