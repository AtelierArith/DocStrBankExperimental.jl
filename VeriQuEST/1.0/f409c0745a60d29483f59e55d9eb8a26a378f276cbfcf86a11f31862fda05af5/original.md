```
compute_angle_δᵥ(::ComputationRound,::NoInputQubits,ϕ,Sx,Sz,θᵥ,rᵥ)
```

Compute the angle δᵥ based on the given parameters.

Computation of δᵥ Case

4. Round ≡ Computation ∩ Qubit ∉ Input set  → δᵥ = ϕᵥ′ + θᵥ + rᵥπ

# Arguments

  * `::ComputationRound`: The computation round.
  * `::NoInputQubits`: The number of input qubits.
  * `ϕ`: The value of ϕ.
  * `Sx`: The value of Sx.
  * `Sz`: The value of Sz.
  * `θᵥ`: The value of θᵥ.
  * `rᵥ`: The value of rᵥ.

# Returns

  * `δᵥ`: The computed angle δᵥ.

# Example

```julia
julia> compute_angle_δᵥ(ComputationRound(),NoInputQubits(),0,0,[0,0,0],0,0)
0
```
