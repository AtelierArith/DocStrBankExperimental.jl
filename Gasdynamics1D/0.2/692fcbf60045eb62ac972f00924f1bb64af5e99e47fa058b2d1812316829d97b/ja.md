```
Pressure(p0::StagnationPressure,M::MachNumber,Isentropic[;gas=Air])
```

停滞圧 `p0` とマッハ数 `M` に対応する圧力を計算します。

$$
p = p_0 \left( 1 + \dfrac{\gamma-1}{2} M^2\right)^{-\gamma/(\gamma-1)}
$$

`Isentropic` 引数を省略することもできます、`Temperature(T0,M)`。
