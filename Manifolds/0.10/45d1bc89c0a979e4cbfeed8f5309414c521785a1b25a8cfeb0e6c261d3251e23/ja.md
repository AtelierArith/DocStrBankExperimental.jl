```
inner(M::Grassmann, p, X, Y)
```

点 `p` の接空間からの二つの接ベクトル `X`, `Y` の内積を計算します。式は次のようになります。

$$
g_p(X,Y) = \operatorname{tr}(X^{\mathrm{H}}Y),
$$

ここで、$⋅^{\mathrm{H}}$ は複素共役転置またはエルミートを示します。
