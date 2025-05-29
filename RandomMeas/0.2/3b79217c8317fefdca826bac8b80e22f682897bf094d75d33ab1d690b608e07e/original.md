```
get_Born_MPS(ρ::MPO)
```

Construct the Born probability vector as an MPS from an MPO representation of a density matrix ρ.

This function computes the Born probability vector P(s) = ⟨s|ρ|s⟩, where |s⟩ is a basis state. It does so by contracting each tensor of the MPO ρ with appropriate delta tensors that enforce equality between the unprimed and primed indices. The result is returned as an MPS that represents the Born probabilities over the computational basis.

# Arguments

  * `ρ::MPO`: A Matrix Product Operator representing the density matrix.

# Returns

An MPS representing the Born probability vector.

# Example

```julia
P = get_Born_MPS(ρ)
```
