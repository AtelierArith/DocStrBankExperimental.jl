```
MachNumber(T_over_T0::TemperatureRatio,Isentropic[;gas=Air])
```

温度と停滞温度の比 `T_over_T0` に対応するマッハ数を計算します。

$$
M = \left( \dfrac{2}{\gamma-1}\left(\dfrac{1}{T/T_0} - 1 \right)\right)^{1/2}
$$

`Isentropic` 引数を省略することもでき、`MachNumber(T_over_T0)` とすることができます。また、`T` と `T0` の引数を別々に指定することも可能です。`MachNumber(T,T0)`
