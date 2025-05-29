```
freeprecess(t, M0, T1, T2, Δf)
```

Simulate free-precession, i.e., relaxation and off-resonance precession. Returns `(A, B)` such that `A * M + B` applies free-precession to the magnetization `M`.

For an in-place version, see [`freeprecess!`](@ref).

# Arguments

  * `t::Real`: Duration of free-precession (ms)
  * `M0::Real`: Equilibrium magnetization
  * `T1::Real`: Spin-lattice recovery time constant (ms)
  * `T2::Real`: Spin-spin recovery time constant (ms)
  * `Δf::Real`: Off-resonance frequency (Hz)

# Examples

```jldoctest
julia> (A, B) = freeprecess(100, 1, 1000, 100, 3.75); A * Magnetization(1, 0, 0) + B
Magnetization vector with eltype Float64:
 Mx = -0.2601300475114444
 My = -0.2601300475114445
 Mz = 0.09516258196404048
```
