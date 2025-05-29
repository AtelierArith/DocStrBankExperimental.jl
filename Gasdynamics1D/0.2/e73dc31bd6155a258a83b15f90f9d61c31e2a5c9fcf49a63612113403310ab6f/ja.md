```
MachNumber(p_over_p0::PressureRatio,Isentropic[;gas=Air])
```

圧力と停滞圧力の比 `p_over_p0` に対応するマッハ数を計算します。

$$
M = \left( \dfrac{2}{\gamma-1}\left(\dfrac{1}{(p/p_0)^{(\gamma-1)/\gamma}} - 1 \right)\right)^{1/2}
$$

`p` と `p0` の引数を別々に指定することもできます。`MachNumber(p,p0)`
