```
inner(M::GeneralizedStiefel, p, X, Y)
```

2つの接ベクトル `X`、`Y` の内積を計算します。これらは [`GeneralizedStiefel`](@ref) 多様体 `M` の点 `p` の接空間からのものです。式は次のようになります。

$$
(X, Y)_p = \operatorname{trace}(v^{\mathrm{H}}Bw),
$$

すなわち、埋め込みからのスカラー積 `B` によって誘導される計量が接空間に制限されます。
