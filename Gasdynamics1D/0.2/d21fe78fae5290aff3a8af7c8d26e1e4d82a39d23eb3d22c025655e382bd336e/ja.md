```
    P0OverP(M::MachNumber,Isentropic[;gas=PerfectGas]) -> PressureRatio
```

マッハ数 `M` に対する停滞圧と圧力の比を計算します。

$$
\dfrac{p_0}{p} = \left(1 + \dfrac{\gamma-1}{2}M^2 \right)^{\gamma/(\gamma-1)}
$$
