```
mod(x::AbsSimpleNumFieldOrderElem, I::AbsNumFieldOrderIdeal)
```

$$
x
$$

に対して$I$に関して$x \equiv y \bmod I$を満たす$x$の周囲の順序の一意の要素$y$を返します。さらに、$a_1,\dotsc,a_d \in \mathbf{Z}_{\geq 1}$が$I$の一意のHNF基底行列の対角成分であり、$(b_1,\dotsc,b_d)$が$y$の係数ベクトルであるとき、$1 \leq i \leq d$に対して$0 \leq b_i < a_i$となります。
