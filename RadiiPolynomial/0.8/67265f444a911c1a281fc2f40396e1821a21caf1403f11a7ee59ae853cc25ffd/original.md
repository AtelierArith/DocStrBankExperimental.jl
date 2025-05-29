```
algebraicweight(a::Sequence{<:SequenceSpace})
```

Compute an approximation of the algebraic decay rate of `a` by performing the ordinary least squares method on the logarithm of the absolute value of the coefficients of `a`.

See also: [`AlgebraicWeight`](@ref), [`IdentityWeight`](@ref), [`GeometricWeight`](@ref), [`geometricweight`](@ref) and [`BesselWeight`](@ref).

# Examples

```jldoctest
julia> rate(algebraicweight(Sequence(Taylor(10), [inv((1.0 + i)^2) for i in 0:10]))) ≈ 2
true

julia> rate.(algebraicweight(Sequence(Taylor(10) ⊗ Fourier(3, 1.0), vec([inv((1.0 + i)^2 * (1.0 + abs(j))^3) for i in 0:10, j in -3:3])))) .≈ (2, 3)
(true, true)
```
