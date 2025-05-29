```
freeprecess(spin, t, [nothing])
freeprecess(spinmc, t, [workspace])
freeprecess(spin, t, grad, [nothing])
freeprecess(spinmc, t, grad, [workspace])
```

Simulate free-precession for the given spin for time `t` ms, optionally in the presence of a B0 gradient. Returns `(A, B)` such that `A * M + B` applies free-precession to the magnetization `M`.

For `SpinMC` objects, `workspace isa BlochMcConnellWorkspace`. Pass in `nothing` instead to use an approximate matrix exponential to solve the Bloch-McConnell equation.

For an in-place version, see [`freeprecess!`](@ref).

# Examples

```jldoctest
julia> s = Spin(Magnetization(1, 0, 0), 1, 1000, 100, 3.75)
Spin{Float64}:
 M = Magnetization(1.0, 0.0, 0.0)
 M0 = 1.0
 T1 = 1000.0 ms
 T2 = 100.0 ms
 Δf = 3.75 Hz
 pos = Position(0.0, 0.0, 0.0) cm

julia> (A, B) = freeprecess(s, 100); A * s.M + B
Magnetization vector with eltype Float64:
 Mx = -0.2601300475114444
 My = -0.2601300475114445
 Mz = 0.09516258196404048

julia> s = Spin(Magnetization(1, 0, 0), 1, 1000, 100, 0, Position(0, 0, 3.75))
Spin{Float64}:
 M = Magnetization(1.0, 0.0, 0.0)
 M0 = 1.0
 T1 = 1000.0 ms
 T2 = 100.0 ms
 Δf = 0.0 Hz
 pos = Position(0.0, 0.0, 3.75) cm

julia> (A, B) = freeprecess(s, 100, Gradient(0, 0, 1/GAMBAR)); A * s.M + B
Magnetization vector with eltype Float64:
 Mx = -0.2601300475114444
 My = -0.2601300475114445
 Mz = 0.09516258196404048
```
