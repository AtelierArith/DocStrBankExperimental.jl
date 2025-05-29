```
SupersonicMachNumber(A_over_Astar::AreaRatio,Isentropic[;gas=Air]) -> MachNumber
```

与えられた面積と音速面積の比 `A_over_Astar` に対して超音速マッハ数を計算するには、次の方程式を解きます。

$$
\dfrac{A}{A^*} = \dfrac{1}{M} \left( \dfrac{2}{\gamma+1} \left( 1 + \dfrac{\gamma-1}{2}M^2\right)\right)^{(\gamma+1)/2/(\gamma-1)}
$$
