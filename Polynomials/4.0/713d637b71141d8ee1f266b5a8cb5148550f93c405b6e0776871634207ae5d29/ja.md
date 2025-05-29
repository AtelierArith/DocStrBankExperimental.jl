```
printpoly(io::IO, p::AbstractPolynomial, mimetype = MIME"text/plain"(); descending_powers=false, offset::Int=0, var=indeterminate(p), compact=false, mulsymbol="*")
```

多項式 `p` の人間が読みやすい表現を `io` に出力します。MIME タイプ "text/plain"（デフォルト）、"text/latex"、および "text/html" がサポートされています。デフォルトでは、項は昇順の累乗の順序で、`coeffs(p)` の順序に一致します。`descending_powers=true` を指定すると、順序が逆になります。`offset` は、印刷のために指数に加算される整数を許可します。`var` は、印刷に使用される変数を上書きすることを許可します。`mulsymbol=""` を設定すると、演算子が印刷されないようになります。`compact=true` を設定すると、浮動小数点数のコンパクトスタイルが使用されます。

# 例

```jldoctest show
julia> using Polynomials

julia> printpoly(stdout, Polynomial([1,2,3], :y))
1 + 2*y + 3*y^2

julia> printpoly(stdout, Polynomial([1,2,3], :y), descending_powers=true)
3*y^2 + 2*y + 1

julia> printpoly(stdout, Polynomial([2, 3, 1], :z), descending_powers=true, offset=-2)
1 + 3*z^-1 + 2*z^-2

julia> printpoly(stdout, Polynomial([-1, 0, 1], :z), offset=-1, descending_powers=true)
z - z^-1

julia> printpoly(stdout, Polynomial([-1, 0, 1], :z), offset=-1, descending_powers=true, var=:x)
x - x^-1

julia> p = Polynomial([sqrt(i) for i in 1:4])
Polynomial(1.0 + 1.4142135623730951*x + 1.7320508075688772*x^2 + 2.0*x^3)

julia> printpoly(stdout, p, compact=true)
1.0 + 1.41421*x + 1.73205*x^2 + 2.0*x^3

julia> printpoly(stdout, map(x -> round(x, digits=12), p))  # more control on rounding
1.0 + 1.414213562373*x + 1.732050807569*x^2 + 2.0*x^3
```
