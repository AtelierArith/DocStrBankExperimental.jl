Returns the qubit density matrix for quantum state described by a coordinate on bloch sphere. See [`bloch_qubit_ket`](@ref)

Spherical Coordinates:

States on the surface of bloch sphere may be described by spherical coordinates.

```julia
bloch_qubit_state(θ::Real, ϕ::Real) :: State{Complex{Float64}}
```

  * `θ ∈ [0, π]`: polar angle (w.r.t z-axis).
  * `ϕ ∈ [0, 2π]`: azimuthal angle (x-y plane)

Cartesian Coordinates:

States within the volume of bloch sphere may be described in cartesian coordinates.

```julia
bloch_qubit_state(x::Real, y::Real, z::Real) :: State{Complex{Float64}}
```

  * where `x`, `y`, and `z` are constrained to the unit sphere, `0 <= norm([x,y,z]) <= 1`.

A `DomainError` is thrown if the coordinates `(x,y,z)` do  not adhere to constraints.
