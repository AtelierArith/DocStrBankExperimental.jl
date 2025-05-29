```
DiscreteChebyshev
```

これは、*非*直交多項式の二パラメータファミリーを定義するために、[Koepf and Schmersau](https://arxiv.org/pdf/math/9703217.pdf) のp22を使用します。

```jldoctest
julia> using Polynomials, SpecialPolynomials

julia> import SpecialPolynomials: Δₓ, ∇ₓ

julia> α,β = 1/2, 1
(0.5, 1)

julia> P  = DiscreteChebyshev{α,β}
Polynomials.MutableDensePolynomial{SpecialPolynomials.DiscreteChebyshevBasis{0.5, 1}}

julia> i = 5
5

julia> yᵢ = basis(P, i)
DiscreteChebyshev{0.5,1}(1.0⋅K⁽ᵅᵝ⁾₅(x))

julia> x = variable(P)
DiscreteChebyshev{0.5,1}(- 2.0⋅K⁽ᵅᵝ⁾₀(x) + 2.0⋅K⁽ᵅᵝ⁾₁(x))

julia> a,b,c,d,e = SpecialPolynomials.abcde(P)
(a = 0, b = 0, c = 1, d = 0.5, e = 1)

julia> λᵢ  = -(a*i*(i-1)  + d*i)
-2.5

julia> Δₓ(∇ₓ(yᵢ)) +  (α*x + β) * Δₓ(yᵢ) ≈ -λᵢ*yᵢ # p22: "are not orthogonal, but satisfy the difference equation..."
true
```
