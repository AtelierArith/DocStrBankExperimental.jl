```
get_selfXEB(ψ::MPS)
```

Compute the self-XEB (cross-entropy benchmarking) metric for a pure state represented as an MPS.

The self-XEB is defined as:

```
selfXEB = 2^N * ∑ₛ |ψ(s)|⁴ - 1
```

where the sum is over all computational basis states s and N is the number of sites (qubits). This function first computes the Born probability MPS from ψ, then calculates the inner product of the probability MPS with itself, scales the result by 2^N, and finally subtracts 1.

# Arguments

  * `ψ::MPS`: A Matrix Product State representing a pure quantum state.

# Returns

A scalar (Float64) representing the self-XEB value.

# Example

```julia
x = get_selfXEB(ψ)
```
