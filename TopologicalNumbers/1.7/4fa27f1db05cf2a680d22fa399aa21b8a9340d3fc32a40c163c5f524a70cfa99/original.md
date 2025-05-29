```
WPProblem(H, N)
```

Constructs a problem for calculating the Weyl points with the default parameters.

# Arguments

  * `H`: The Hamiltonian function `H=H(k)` that defines the system. `k` is a abstract vector (or a tuple) of the wavenumber vector. Dimension of `k` must be 3.
  * `N`: The number of meshes when discretizing the Brillouin Zone. The $n$th iteration divides the Brillouin zone into $1/N^n$.

# Returns

A `WPProblem` object.

# Example

```julia
julia> 
```
