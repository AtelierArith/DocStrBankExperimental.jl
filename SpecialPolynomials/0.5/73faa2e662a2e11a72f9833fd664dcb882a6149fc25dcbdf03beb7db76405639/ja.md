```
Chebyshev{<:Number}(coeffs::AbstractVector, var=:x)
```

[Chebyshev](https://en.wikipedia.org/wiki/Chebyshev_polynomials) 多項式の第一種。これらは定義域 $(-1,1)$ と重み関数 $1/\sqrt{1-x^2}$ を持ちます。

多項式はその係数 `a` から構築され、最低次の項が最初に来ます。オプションで、指定された変数 `x` に関して構築されます。`x` は文字、シンボル、または文字列であることができます。

# 例

```jldoctest
julia> using Polynomials, SpecialPolynomials

julia> Chebyshev([1, 0, 3, 4])
Chebyshev(1⋅T₀(x) + 3⋅T₂(x) + 4⋅T₃(x))

julia> Chebyshev([1, 2, 3, 0], :s)
Chebyshev(1⋅T₀(s) + 2⋅T₁(s) + 3⋅T₂(s))

julia> one(Chebyshev)
Chebyshev(1.0⋅T₀(x))
```

!!! note
    これは、Miles Lucas による `Polynomials` パッケージの `ChebyshevT` の例からコピーされたものです。


!!! note
    [Amparo Gil, Javier Segura, and Nico Temme による "Numerical Methods for Special Functions" のオンラインで利用可能なサンプル章](https://archive.siam.org/books/ot99/OT99SampleChapter.pdf) は、これらの多項式の非常に良い概要を提供しています。

