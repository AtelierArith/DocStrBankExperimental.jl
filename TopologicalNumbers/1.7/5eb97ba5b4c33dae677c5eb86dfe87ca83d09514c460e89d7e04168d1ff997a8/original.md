```
LBFProblem(H, n, N)
```

Constructs a local Berry flux problem with the default parameters.

# Arguments

  * `H`: The Hamiltonian function `H=H(k)` that defines the system. `k` is a abstract vector (or a tuple) of the wavenumber vector. Dimension of `k` must be 2.
  * `n`: An `AbstractVector` (or a `Tuple`) including two elements of `Int`, which represents wavenumber ($2\pi n/N$) when calculating Berry flux. Dimension of `n` must be 2.
  * `N`: The number of points for one direction in the Brillouin zone.

# Returns

A `LBFProblem` object.

# Example

```julia
julia> 
```
