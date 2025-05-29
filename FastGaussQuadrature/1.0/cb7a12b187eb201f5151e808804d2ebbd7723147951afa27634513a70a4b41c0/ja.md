```
gaussradau(n::Integer) -> x, w  # ノード、重み
```

[ガウス-ラドー数値積分](https://mathworld.wolfram.com/RadauQuadrature.html)のノード `x` と重み `w` を返します。

$$
\int_{-1}^{1} f(x) dx \approx \sum_{i=1}^{n} w_i f(x_i)
$$

# 例

```jldoctest
julia> x, w = gaussradau(3);

julia> f(x) = x^4;

julia> I = dot(w, f.(x));

julia> I ≈ 2/5
true
```

最初のノードは -1 に固定されていることに注意してください。

```jldoctest
julia> x, w = gaussradau(3);

julia> x[1]
-1.0
```
