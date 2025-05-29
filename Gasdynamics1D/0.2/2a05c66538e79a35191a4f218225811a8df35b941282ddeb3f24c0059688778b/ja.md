```
AStar(A::Area,M::MachNumber,Isentropic[;gas=Air]) -> Area
```

与えられた面積 `A` とマッハ数 `M` に対して音速面積を計算します。

$$
A^* = A M \left( \dfrac{2}{\gamma+1} \left( 1 + \dfrac{\gamma-1}{2}M^2\right)\right)^{-(\gamma+1)/2/(\gamma-1)}
$$

`Isentropic` 引数は省略できます。
