```
get_Born_MPS(ψ::MPS)
```

Construct the Born probability vector P(s) = |ψ(s)|² as an MPS from an MPS representation ψ.

This function computes the probability for each computational basis state by contracting each tensor of the MPS ψ with its complex conjugate, using appropriate delta tensors to enforce index equality. The resulting MPS represents the Born probability distribution of the state.

# Arguments

  * `ψ::MPS`: A matrix product state representing a pure quantum state.

# Returns

An MPS representing the Born probability vector, where each tensor P[i] corresponds to the probability contribution at site i.

# Example

```julia
P = get_Born_MPS(ψ)
```
