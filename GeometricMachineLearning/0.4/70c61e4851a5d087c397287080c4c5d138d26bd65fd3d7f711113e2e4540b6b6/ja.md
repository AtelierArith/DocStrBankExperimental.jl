```
GrassmannLayer(n, N)
```

`GrassmannLayer`のインスタンスを作成します。

このレイヤーは、Grassmann多様体の要素との単純な乗算を行います。すなわち、

$$
    \mathtt{GrassmannLayer}: x \mapsto Ax,
$$

ここで、$A$はGrassmann多様体の要素の表現であり、すなわち$\mathcal{A} = \mathrm{span}(A)$です。
