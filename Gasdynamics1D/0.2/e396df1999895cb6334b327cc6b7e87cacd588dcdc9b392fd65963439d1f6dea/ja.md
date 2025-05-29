```
MachNumber(A_over_Astar::AreaRatio,Isentropic[;gas=Air]) -> MachNumber, MachNumber
```

与えられた面積と音速面積の比 `A_over_Astar` に対して、次の方程式を解くことによって亜音速および超音速のマッハ数を計算します。

$$
\dfrac{A}{A^*} = \dfrac{1}{M} \left( \dfrac{2}{\gamma+1} \left( 1 + \dfrac{\gamma-1}{2}M^2\right)\right)^{(\gamma+1)/2/(\gamma-1)}
$$

`Isentropic` 引数は省略できます。
