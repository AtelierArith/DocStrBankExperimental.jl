```
StagnationTemperature(ρ0::StagnationDensity,p0::StagnationPressure[;gas=Air])
```

停滞密度 `ρ0` と停滞圧 `p0` から停滞温度を計算します。使用する式は次の通りです。

$$
T_0 = p_0/(\rho_0 R)
$$

引数の順序を入れ替えることもできます。
