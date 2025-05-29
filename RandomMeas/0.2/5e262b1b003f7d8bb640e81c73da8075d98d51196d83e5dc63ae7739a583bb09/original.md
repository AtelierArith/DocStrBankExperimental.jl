```
get_trace_moment(spec::ITensor, k::Int)
```

Compute the kth moment of the entanglement spectrum represented by the ITensor `spec`.

The function assumes that `spec` is a square ITensor whose diagonal elements correspond to the singular values (Schmidt coefficients) of a reduced density matrix. The kth moment is computed as:

```
pk = ∑ₗ (spec[l, l]^(2*k))
```

which effectively computes the sum over the kth powers of the squared singular values.

# Arguments

  * `spec::ITensor`: A square ITensor representing the entanglement spectrum.
  * `k::Int`: The moment order to compute (must be an integer ≥ 1).

# Returns

A scalar (Float64) corresponding to the kth moment.

# Example

```julia
moment = get_trace_moment(spec, 2)
```
