```
StagnationTemperature(T::Temperature,M::MachNumber,Isentropic[;gas=Air])
```

温度 `T` とマッハ数 `M` に対応する停滞温度を計算します。

$$
T_0 = T \left( 1 + \dfrac{\gamma-1}{2} M^2\right)
$$

`Isentropic` 引数を省略することもでき、`StagnationTemperature(T,M)` として使用できます。
