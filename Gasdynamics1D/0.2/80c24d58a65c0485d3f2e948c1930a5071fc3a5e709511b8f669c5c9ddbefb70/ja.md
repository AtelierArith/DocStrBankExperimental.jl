```
P0OverP0Star(M::MachNumber,FannoFlow[;gas=PerfectGas]) -> StagnationPressureRatio
```

ファノ流におけるマッハ数 `M` から、停滞圧力と音速停滞圧力の比を計算します。

$$
\dfrac{p_0}{p_0^*} = \dfrac{1}{M} \left(\dfrac{2+(\gamma-1)M^2}{\gamma+1}\right)^{(\gamma+1)/2/(\gamma-1)}
$$
