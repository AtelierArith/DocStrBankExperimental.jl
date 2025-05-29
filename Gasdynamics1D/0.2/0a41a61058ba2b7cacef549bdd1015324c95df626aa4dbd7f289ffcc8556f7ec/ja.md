```
MachNumber(fL_over_D::FLOverD,FannoFlow[;gas=Air]) -> MachNumber, MachNumber
```

与えられた摩擦係数と音速点までの距離の比 `fL_over_D` に基づいて、亜音速および超音速のマッハ数を計算します。この方程式を解くことによって、

$$
\dfrac{fL^*}{D} = \dfrac{1-M^2}{\gamma M^2} + \dfrac{\gamma+1}{2\gamma} \ln \left(\dfrac{(\gamma+1)M^2}{2+(\gamma-1)M^2}\right)
$$
