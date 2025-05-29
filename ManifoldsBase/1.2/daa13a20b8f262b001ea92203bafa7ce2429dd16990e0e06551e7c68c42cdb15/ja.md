```
change_representer(M::AbstractManifold, G2::AbstractMetric, p, X)
```

線形関数の表現者 `X`（言い換えれば `p` における余接ベクトル）を、[`AbstractManifold`](@ref) `M` の `p` における接空間で、[`AbstractMetric`](@ref) `G2` に関して与えられたものから、`M` の（暗黙的な）計量に関する表現者に変換します。

`X` を `M` の（暗黙的に与えられた）計量 $g_1$ に関する表現者に変換するためには、次のような変換関数 $c: T_p\mathcal M \to T_p\mathcal M$ を見つける必要があります。

$$
    g_2(X,Y) = g_1(c(X),Y)
$$
