```
bloch_qubit_ket( θ :: Real, ϕ :: Real ) :: Ket{Complex{Float64}}
```

Returns the qubit ket for the specified spherical coordinate on the surface of bloch sphere, `(r=1, θ, ϕ)`:

$$
|\psi\rangle = \cos(\theta/2)|0\rangle + e^{i\phi}\sin(\theta/2)|1\rangle
$$

If the ket does not have a phase then a real-valued `Ket` is constructed as:

```julia
bloch_qubit_ket( θ :: Real ) :: Ket{Float64}
```

Inputs:

  * `θ ∈ [0, 2π]`: polar angle (w.r.t z-axis)
  * `ϕ ∈ [0, 2π]`: azimuthal angle (x-y plane)

A `DomainError` is thrown if inputs `θ` and/or `ϕ` do are not within the valid range.
