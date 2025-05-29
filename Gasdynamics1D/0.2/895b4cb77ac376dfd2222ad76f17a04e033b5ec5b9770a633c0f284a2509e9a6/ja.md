```
P0OverP0Star(M::MachNumber,RayleighFlow[;gas=Air]) -> PressureRatio
```

与えられたマッハ数に対して、レイリー流のための停滞圧と音速停滞圧の比を計算します。使用する方程式は次のとおりです。

$$
\dfrac{p_0}{p_0^*} = \dfrac{(\gamma+1)}{1+\gamma M^2} \left[ \left( \dfrac{1}{\gamma+1} \right)\left(2 + (\gamma-1) M^2\right)\right]^{\gamma/(\gamma-1)}
$$
