```
AOverAStar(M::MachNumber,Isentropic[;gas=Air]) -> AreaRatio
```

与えられたマッハ数 `M` に対して、音速面に対する局所面積の比を計算します。

$$
\dfrac{A}{A^*} = \dfrac{1}{M} \left( \dfrac{2}{\gamma+1} \left( 1 + \dfrac{\gamma-1}{2}M^2\right)\right)^{(\gamma+1)/2/(\gamma-1)}
$$

`Isentropic` 引数は省略できます。
