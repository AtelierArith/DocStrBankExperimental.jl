```
    T0OverT(M::MachNumber,Isentropic[;gas=PerfectGas]) -> TemperatureRatio
```

マッハ数 `M` に対する停滞温度と温度の比を計算します。

$$
\dfrac{T_0}{T} = 1 + \dfrac{\gamma-1}{2}M^2
$$

`Isentropic` 引数を省略することもでき、`T0OverT(M)` となります。
