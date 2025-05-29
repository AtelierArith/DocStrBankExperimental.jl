```
FreePrecessionMatrix(E1, E2, θ)
FreePrecessionMatrix{T}()
FreePrecessionMatrix()
```

Create a mutable `FreePrecessionMatrix` object encoding the effects of relaxation and off-resonance precession.

# Properties

  * `E1::Real`: T1 relaxation
  * `E2::Real`: T2 relaxation
  * `θ::Real`: Angle of off-resonance precession (rad)

# Examples

```jldoctest
julia> T1 = 1000; T2 = 100; Δω = π/600; t = 100;

julia> F = FreePrecessionMatrix(exp(-t / T1), exp(-t / T2) * cos(Δω * t), exp(-t / T2) * sin(Δω * t))
FreePrecessionMatrix{Float64}:
 E1 = 0.9048374180359595
 E2 = 0.31859294158449203
 θ = 0.18393972058572114 rad

julia> Matrix(F)
3×3 Matrix{Float64}:
  0.313219  0.058272  0.0
 -0.058272  0.313219  0.0
  0.0       0.0       0.904837
```
