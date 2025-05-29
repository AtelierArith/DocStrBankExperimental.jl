```
Newton{N,S,T,X}
```

A [Newton](https://en.wikipedia.org/wiki/Newton_polynomial) interpolating polynomial uses a basis `1`, `(x-x_0)`, `(x-x_0)(x-x_1)`, ..., `(x-x0)(x-x1)⋅⋅⋅(x-x_{n-1})` and coefficients (in forward form) `f[x_0]`, `f[x_0,x_1]`, ...,`f[x_0,...,x_n]`. The Newton class stores the nodes (after sorting) and the Newton tableau used to generate the coefficients on fitting.

The easiest way to construct an instance is with `fit`, as in:

```jldoctest Newton
julia> using Polynomials, SpecialPolynomials

julia> xs = [1,2,3,4]; f(x)= x^3 - 2x + 1;

julia> p = fit(Newton, xs, f)
Newton(5.0⋅p_1(x) + 6.0⋅p_2(x) + 1.0⋅p_3(x))

julia> p.(xs) == f.(xs)  # p interpolates
true

julia> convert(Polynomial, p)
Polynomial(1.0 - 2.0*x + 1.0*x^3)
```
