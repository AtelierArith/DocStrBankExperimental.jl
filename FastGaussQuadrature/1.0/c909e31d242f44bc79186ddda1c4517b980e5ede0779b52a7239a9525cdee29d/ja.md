```
gausslobatto(n::Integer) -> x, w  # ノード、重み
```

ノード `x` と重み `w` を返します [ガウス・ロバット数値積分](https://mathworld.wolfram.com/LobattoQuadrature.html)。

$$
\int_{-1}^{1} f(x) dx \approx \sum_{i=1}^{n} w_i f(x_i)
$$

# 例

```jldoctest
julia> x, w = gausslobatto(4);

julia> f(x) = x^4;

julia> I = dot(w, f.(x));

julia> I ≈ 2/5
true
```

ノードの両端は -1 と 1 に固定されていることに注意してください。

```jldoctest
julia> x, w = gausslobatto(4);

julia> x[1], x[end]
(-1.0, 1.0)
```
