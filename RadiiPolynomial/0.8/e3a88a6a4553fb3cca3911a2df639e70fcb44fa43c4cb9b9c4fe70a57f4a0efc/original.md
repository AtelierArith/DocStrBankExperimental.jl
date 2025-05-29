```
geometricweight(a::Sequence{<:SequenceSpace})
```

Compute an approximation of the geometric decay rate of `a` by performing the ordinary least squares method on the logarithm of the absolute value of the coefficients of `a`.

See also: [`GeometricWeight`](@ref), [`IdentityWeight`](@ref), [`AlgebraicWeight`](@ref), [`algebraicweight`](@ref) and [`BesselWeight`](@ref).

# Examples

```jldoctest
julia> rate(geometricweight(Sequence(Taylor(10), [inv(2.0^i) for i in 0:10]))) ≈ 2
true

julia> rate.(geometricweight(Sequence(Taylor(10) ⊗ Fourier(3, 1.0), vec([inv(2.0^i * 3.0^abs(j)) for i in 0:10, j in -3:3])))) .≈ (2, 3)
(true, true)
```
