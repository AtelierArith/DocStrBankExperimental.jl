```
exp(M::AbstractManifold, p, X)
```

多様体 [`AbstractManifold`](@ref) `M` の点 `p` における接ベクトル `X` の指数写像を計算します。すなわち、

$$
\exp_p X = γ_{p,X}(1),
$$

ここで $γ_{p,X}$ は $γ(0)=p$ から始まり、$\dot γ(0) = X$ となる唯一の測地線です。

また、[`shortest_geodesic`](@ref) や [`retract`](@ref) も参照してください。 ```
