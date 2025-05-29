```
inner(M::ProbabilitySimplex, p, X, Y)
```

2つの接ベクトル `X`、`Y` の内積を計算します。これらは点 `p` における接空間 $T_pΔ^n$ からのものです。式は次のようになります。

$$
g_p(X,Y) = \sum_{i=1}^{n+1}\frac{X_iY_i}{p_i}
$$

`M` が境界を含む場合、$p_i$ が 0 に等しい座標は単にスキップできます。詳細は [AyJostLeSchwachhoefer:2017](@cite) の命題 2.1 を参照してください。
