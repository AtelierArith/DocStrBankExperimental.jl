```
gaussian_entropy(H::Symmetric{T}) where T <: Real
```

Calculate the entropy of a Gaussian distribution with Hessian (i.e. negative precision) matrix `H`.

# Arguments

  * `H::Symmetric{T}`: The Hessian matrix.

# Returns

  * The entropy of the Gaussian distribution.
