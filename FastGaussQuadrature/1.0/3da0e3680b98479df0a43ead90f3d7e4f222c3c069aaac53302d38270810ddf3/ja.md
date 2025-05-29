```
gausshermite(n::Integer; normalize = false) -> x, w  # ノード、重み
```

[ガウス・エルミート数値積分](https://en.wikipedia.org/wiki/Gauss%E2%80%93Hermite_quadrature)のノード `x` と重み `w` を返します。

$$
\int_{-\infty}^{+\infty} f(x) \exp(-x^2) dx \approx \sum_{i=1}^{n} w_i f(x_i)
$$

オプション `normalize=true` は次のように計算します。

$$
\int_{-\infty}^{+\infty} f(x) \phi(x) dx \approx \sum_{i=1}^{n} w_i f(x_i),
$$

ここで、$\phi$ は標準正規密度関数です。

# 例

```jldoctest
julia> x, w = gausshermite(3);

julia> f(x) = x^4;

julia> I = dot(w, f.(x));

julia> I ≈ 3(√π)/4
true
```
