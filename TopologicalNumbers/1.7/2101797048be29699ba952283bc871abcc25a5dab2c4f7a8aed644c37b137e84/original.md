```
WCSProblem(H, kn)
```

Constructs a problem for finding and calculating the Weyl points with the default parameters.

# Arguments

  * `H`: The Hamiltonian function `H=H(k)` that defines the system. `k` is a abstract vector (or a tuple) of the wavenumber vector. Dimension of `k` must be 3.
  * `kn`: Compute the Chern number of the plane perpendicular to the `"kn"` direction in Brillouin zone (`"k1"`, `"k2"`, `"k3"`).

# Returns

A `WCSProblem` object.

# Example

```julia
julia> 
```
