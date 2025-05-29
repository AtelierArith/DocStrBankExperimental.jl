```
Dispersion(; dispersion=nothing, dispersion_inverse=nothing)
```

Equivalence to convert between temporal and spatial frequencies using a specific [dispersion relation](https://en.wikipedia.org/wiki/Dispersion_relation).

This extends the Periodic() equivalence to convert between spatial and temporal quantities based on the provided dispersion relation.

See also [`DimensionfulAngles.Periodic`](@ref).

# Example

```jldoctest; filter = r"(\d*).(\d{1,10})\d+" => s"\1.\2"
julia> using DimensionfulAngles, Unitful

julia> g = Unitful.gn  # gravitational acceleration
9.80665 m s⁻²

julia> deepwater = Dispersion(
        dispersion = (k -> √(g*k*θ₀)), dispersion_inverse = (ω -> ω^2/(g*θ₀))
       );

julia> uconvert(u"radᵃ/mm", 1.0u"Hz", deepwater)
0.004025678249387654 rad mm⁻¹
```

Some dispersion relations do not have an expressible inverse. In such cases using `Roots.jl` might be beneficial. For example, here is how we could use the linear [water wave dispersion](https://en.wikipedia.org/wiki/Dispersion_(water_waves)) without deep water approximation:

```jldoctest; filter = r"(\d*).(\d{1,10})\d+" => s"\1.\2"
julia> using DimensionfulAngles, Unitful, Roots

julia> g = Unitful.gn  # gravitational acceleration
9.80665 m s⁻²

julia> k0 = (2π)u"radᵃ/m"  # initial guess: 1m wavelength
6.283185307179586 rad m⁻¹

julia> h = 0.5u"m"  # water depth
0.5 m

julia> waterwaves = Dispersion(
        dispersion = (k -> √(k*θ₀*g*tanh(k*h/θ₀))),
        dispersion_inverse = (ω -> solve(ZeroProblem(k -> k - ω^2/(g*tanh(k*h/θ₀))/θ₀, k0)))
       );

julia> uconvert(u"Hz", 0.004025678249387654u"radᵃ/mm", waterwaves)
0.9823052153509486 Hz

julia> h = (Inf)u"m"  # water depth
Inf m

julia> waterwaves = Dispersion(
        dispersion = ( k -> √(k*θ₀*g*tanh(k*h/θ₀)) ),
        dispersion_inverse = (ω -> solve(ZeroProblem(k -> k - ω^2/(g*tanh(k*h/θ₀))/θ₀, k0)))
       );

julia> uconvert(u"Hz", 0.004025678249387654u"radᵃ/mm", waterwaves) ≈ 1u"Hz"
true
```
