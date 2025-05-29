```
fit(P::Type{<:StandardBasisPolynomial}, x, y, J, [cs::Dict{Int, T}]; weights, var)
```

Using constrained least squares, fit a polynomial of the type `p = ∑_{i ∈ J} aᵢ xⁱ + ∑ cⱼxʲ` where `cⱼ` are fixed non-zero constants

  * `J`: a collection of degrees to find coefficients for
  * `cs`: If given, a `Dict` of key/values, `i => cᵢ`, which indicate the degree and value of the fixed non-zero constants.

The degrees in `cs` and those in `J` should not intersect.

Example

```julia
x = range(0, pi/2, 10)
y = sin.(x)
P = Polynomial
p0 = fit(P, x, y, 5)
p1 = fit(P, x, y, 1:2:5)
p2 = fit(P, x, y, 3:2:5, Dict(1 => 1))
[norm(p.(x) - y) for p ∈ (p0, p1, p2)] # 1.7e-5, 0.00016, 0.000248
```
