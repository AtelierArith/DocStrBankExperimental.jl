```
exp(M::AbstractManifold, p, X)
exp(M::AbstractManifold, p, X, t::Number = 1)
```

接続体 `M` の点 `p` での接ベクトル `X` の指数写像を計算します。オプションで `t` でスケーリングできます。すなわち、

$$
\exp_p X = γ_{p,X}(1),
$$

ここで $γ_{p,X}$ は $γ(0)=p$ から始まり、$\dot γ(0) = X$ となる唯一の測地線です。

他にも [`shortest_geodesic`](@ref)、[`retract`](@ref) を参照してください。
