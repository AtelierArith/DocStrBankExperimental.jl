```
Newton{N,S,T,X}
```

[Newton](https://en.wikipedia.org/wiki/Newton_polynomial) 補間多項式は、基底 `1`、`(x-x_0)`、`(x-x_0)(x-x_1)`、...、`(x-x0)(x-x1)⋅⋅⋅(x-x_{n-1})` と係数（前方形式で） `f[x_0]`、`f[x_0,x_1]`、...、`f[x_0,...,x_n]` を使用します。Newton クラスは、ノード（ソート後）と係数を生成するために使用される Newton テーブルを格納します。

インスタンスを構築する最も簡単な方法は `fit` を使用することです。次のように：

```jldoctest Newton
julia> using Polynomials, SpecialPolynomials

julia> xs = [1,2,3,4]; f(x)= x^3 - 2x + 1;

julia> p = fit(Newton, xs, f)
Newton(5.0⋅p_1(x) + 6.0⋅p_2(x) + 1.0⋅p_3(x))

julia> p.(xs) == f.(xs)  # p は補間します
true

julia> convert(Polynomial, p)
Polynomial(1.0 - 2.0*x + 1.0*x^3)
```
