```
FLStarOverD(M::MachNumber,FannoFlow[;gas=Air])
```

与えられたマッハ数 `M` に対して、音速点までの摩擦係数と距離を直径で割った値を計算します。使用する方程式は次の通りです。

$$
\dfrac{fL^*}{D} = \dfrac{1-M^2}{\gamma M^2} + \dfrac{\gamma+1}{2\gamma} \ln \left(\dfrac{(\gamma+1)M^2}{2+(\gamma-1)M^2}\right)
$$
