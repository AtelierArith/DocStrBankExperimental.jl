```
Temperature(ρ::Density,p::Pressure[;gas=Air])
```

密度 `ρ` と圧力 `p` から温度を計算します。使用する式は

$$
T = p/(\rho R)
$$

引数の順序を入れ替えることもできます。
