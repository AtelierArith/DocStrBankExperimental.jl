```
exp(M::AbstractSphere, p, X)
```

点 `p` から接線方向 `X` に沿って [`AbstractSphere`](@ref) `M` で発生する大円に従って、`p` からの指数写像を計算します。

$$
\exp_p X = \cos(\lVert X \rVert_p)p + \sin(\lVert X \rVert_p)\frac{X}{\lVert X \rVert_p},
$$

ここで、$\lVert X \rVert_p$ は [`norm`](@ref norm(::AbstractSphere,p,X)) であり、[`AbstractSphere`](@ref) `M` の点 `p` における接空間のノルムです。 ```
