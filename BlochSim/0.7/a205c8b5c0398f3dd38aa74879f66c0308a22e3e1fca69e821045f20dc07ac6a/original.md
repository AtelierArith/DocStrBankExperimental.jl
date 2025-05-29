```
excite(spin, rf::InstantaneousRF, [nothing])
excite(spin, rf::RF, [workspace])
```

Simulate excitation for the given spin. Returns `(A, B)` such that `A * M + B` applies excitation to the magnetization `M`. If `isnothing(B)` (as is the case for `InstantaneousRF`s), then `A * M` applies excitation to `M`.

For `RF` objects, `workspace isa ExcitationWorkspace`. For `SpinMC` objects, use `workspace = ExcitationWorkspace(spin, nothing)` to use an approximate matrix exponential to solve the Bloch-McConnell equation.

For an in-place version, see [`excite!`](@ref).

# Examples

```jldoctest
julia> s = Spin(1, 1000, 100, 3.75); s.M
Magnetization vector with eltype Float64:
 Mx = 0.0
 My = 0.0
 Mz = 1.0

julia> (A,) = excite(s, InstantaneousRF(π/2, π/4)); A * s.M
Magnetization vector with eltype Float64:
 Mx = 0.7071067811865476
 My = -0.7071067811865475
 Mz = 6.123233995736766e-17
```
