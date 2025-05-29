```
SupersonicMachNumber(fL_over_D::FLOverD,FannoFlow[;gas=Air]) -> MachNumber
```

超音速マッハ数を計算します。摩擦係数と音速点までの距離の比である `fL_over_D` を与えられた場合、次の方程式を解くことによって求めます。

$$
\dfrac{fL^*}{D} = \dfrac{1-M^2}{\gamma M^2} + \dfrac{\gamma+1}{2\gamma} \ln \left(\dfrac{(\gamma+1)M^2}{2+(\gamma-1)M^2}\right)
$$
