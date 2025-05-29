```
approx_besselroots(ν::Real, n::Integer) -> Vector{Float64}
```

最初の $n$ 個の [ベッセル関数](https://en.wikipedia.org/wiki/Bessel_function) の根を返します。この関数は12桁の精度のみです。

$$
J_{\nu}(x) = \sum_{m=0}^{\infty}\frac{(-1)^j}{\Gamma(\nu+j+1)j!} \left(\frac{x}{2}\right)^{2j+\nu}
$$

# 例

```jldoctest
julia> ν = 0.3;

julia> roots = approx_besselroots(ν, 10);

julia> zeros = (x -> besselj(ν, x)).(roots);

julia> all(zeros .< 1e-12)
true
```
