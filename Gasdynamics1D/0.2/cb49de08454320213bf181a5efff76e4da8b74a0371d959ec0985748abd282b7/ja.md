```
POverPStar(M::MachNumber,FannoFlow[;gas=PerfectGas]) -> PressureRatio
```

ファノ流におけるマッハ数 `M` から音速圧力に対する圧力の比を計算します。

$$
\dfrac{p}{p^*} = \dfrac{1}{M} \left(\dfrac{1+\gamma}{2+(\gamma-1)M^2}\right)^{1/2}
$$
