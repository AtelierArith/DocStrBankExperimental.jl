```
WNProblem(H, n, N)
```

Constructs a problem for calculating the Weyl nodes with the default parameters.

# Arguments

  * `H`: The Hamiltonian function `H=H(k)` that defines the system. `k` is a abstract vector (or a tuple) of the wavenumber vector. Dimension of `k` must be 3.
  * `n`: An `AbstractVector` (or a `Tuple`) including two elements of `Int`, which represents wavenumber ($2\pi n/N$). Dimension of `n` must be 3.
  * `N`: The number of points for one direction in the Brillouin zone.

# Returns

A `WNProblem` object.

# Example

```julia
julia> 
```
