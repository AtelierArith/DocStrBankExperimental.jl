```
get_trace(ρ::MPO)
```

Compute the trace of a Matrix Product Operator (MPO) ρ by contracting each tensor with a delta function that equates its unprimed and primed indices.

# Arguments

  * `ρ::MPO`: A matrix product operator representing a quantum state or operator.

# Returns

A scalar representing the trace of ρ.

# Example

```julia
t = get_trace(ρ)
```
