```
StagnationPressure(p::Pressure,M::MachNumber,Isentropic[;gas=Air])
```

圧力 `p` とマッハ数 `M` に対応する停滞圧を計算します。使用する式は次の通りです。

$$
p_0 = p \left( 1 + \dfrac{\gamma-1}{2} M^2\right)^{\gamma/(\gamma-1)}
$$

`Isentropic` 引数を省略することもでき、`StagnationTemperature(T,M)` を使用できます。
