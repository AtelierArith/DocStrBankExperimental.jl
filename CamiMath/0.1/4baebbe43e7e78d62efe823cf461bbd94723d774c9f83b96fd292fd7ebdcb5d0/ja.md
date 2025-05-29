```
laguerreL(n::Integer, x::T [; deriv=0 [, msg=true]]) where T<:Real
```

次数 `n` のラゲール多項式、

$$
    L_{n}(x)
    = \frac{1}{n!}e^{x}\frac{d^{n}}{dx^{n}}(e^{-x}x^{n})
    = \sum_{k=0}^{n}(-1)^{k}\binom{n}{n-k}\frac{x^{k}}{k!}
    = \sum_{k=0}^{n}c_k(n)x^{k}
$$

ここで、$c_k(n)$ は [`laguerre_polynom`](@ref) のラゲール係数です。

#### 例:

```
julia> polynom = laguerre_polynom(8); println(polynom)
(1//1, -8//1, 14//1, -28//3, 35//12, -7//15, 7//180, -1//630, 1//40320)

julia> polynomial(polynom, 5)
18029//8064

julia> laguerreL(8, 5)
18029//8064

julia> (xmin, Δx, xmax) = (0, 0.1, 11);
julia> n = 8;
julia> L = [laguerreL(n, x) for x=xmin:Δx:xmax];
julia> f = Float64.(L);
plot_function(f, xmin, Δx, xmax; title="次数 $n$ のラゲール多項式")
```

プロットは `CairomMakie` を使用して作成されます。注：`plot_function` は `CamiXon` パッケージには含まれていません。 ![Image](../assets/laguerreL8.png)
