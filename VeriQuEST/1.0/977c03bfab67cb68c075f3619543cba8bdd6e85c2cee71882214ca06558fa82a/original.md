Computation of δᵥ

This function computes the value of δᵥ based on the given parameters.

Case

3. Round ≡ Computation ∩ Qubit ∈ Input set  → δᵥ = ϕᵥ + (θᵥ + xᵥπ) + rᵥπ

Arguments:

  * `::ComputationRound`: The computation round.
  * `::InputQubits`: The input qubits.
  * `ϕ`: The value of ϕ.
  * `Sx`: The value of Sx.
  * `Sz`: The value of Sz.
  * `θᵥ`: The value of θᵥ.
  * `rᵥ`: The value of rᵥ.
  * `xᵥ`: The value of xᵥ.

Returns:

  * `δᵥ`: The computed value of δᵥ.

# Examples

```julia
julia> compute_angle_δᵥ(ComputationRound(),InputQubits(),0,0,[0,0,0],0,0,0)
0
```
