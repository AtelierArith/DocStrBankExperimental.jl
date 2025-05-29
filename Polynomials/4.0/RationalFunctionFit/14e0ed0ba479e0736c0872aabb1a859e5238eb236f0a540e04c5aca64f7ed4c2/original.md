```
fit(::Type{RationalFunction}, xs::AbstractVector{S}, ys::AbstractVector{T}, m, n; var=:x)
```

Fit a rational function of the form `pq = (a₀ + a₁x¹ + … + aₘxᵐ) / (1 + b₁x¹ + … + bₙxⁿ)` to the data `(x,y)`.

!!! note
    This uses a simple implementation of the Gauss-Newton method to solve the non-linear least squares problem: `minᵦ Σ(yᵢ - pq(xᵢ,β)²`, where `β=(a₀,a₁,…,aₘ,b₁,…,bₙ)`.

    A more rapidly convergent method is used in the `LsqFit.jl` package, and if performance is important, re-expressing the problem for use with that package is suggested.

    Further, if an accurate rational function fit of adaptive degrees is of interest, the `BaryRational.jl` package provides an implementation of the AAA algorithm ("which offers speed, flexibility, and robustness we have not seen in other algorithms" [Nakatsukasa, Sète, Trefethen](https://arxiv.org/pdf/1612.00337.pdf)) and one using Floater-Hormann weights [Floater, Hormann](https://doi.org/10.1007/s00211-007-0093-y) ("that have no real poles and arbitrarily high approximation orders on any real interval, regardless of the distribution of the points")

    The [RationalApproximations](https://github.com/billmclean/RationalApproximations) package also has implementations of the AAA algorithm.

    A python library, [polyrat](https://github.com/jeffrey-hokanson/polyrat), has implementations of other algorithms.


## Example

```julia-repl
julia> x = variable(Polynomial{Float64})
Polynomial(1.0*x)

julia> pq = (1+x)//(1-x)
(1.0 + 1.0*x) // (1.0 - 1.0*x)

julia> xs = 2.0:.1:3;

julia> ys = pq.(xs);

julia> v = fit(RationalFunction, xs, ys, 2, 2)
(1.0 + 1.0*x - 6.82121e-13*x^2) // (1.0 - 1.0*x + 2.84217e-13*x^2)

julia> maximum(abs, v(x)-pq(x) for x ∈ 2.1:0.1:3.0)
1.06314956838105e-12

julia> using BaryRational

julia> u = aaa(xs,ys)
(::BaryRational.AAAapprox{Vector{Float64}}) (generic function with 1 method)

julia> maximum(abs, u(x)-pq(x) for x ∈ 2.1:0.1:3.0)
4.440892098500626e-16

julia> u(variable(pq)) # to see which polynomial is used
(2.68328 + 0.447214*x - 1.78885*x^2 + 0.447214*x^3) // (2.68328 - 4.91935*x + 2.68328*x^2 - 0.447214*x^3)
```
