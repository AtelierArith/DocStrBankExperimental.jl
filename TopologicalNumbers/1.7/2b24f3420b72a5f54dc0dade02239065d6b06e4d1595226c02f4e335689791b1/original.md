```
WCSProblem(H, kn, N1, N2)
```

Constructs a problem for finding and calculating the Weyl points with the default parameters.

# Arguments

  * `H`: The Hamiltonian function `H=H(k)` that defines the system. `k` is a abstract vector (or a tuple) of the wavenumber vector. Dimension of `k` must be 3.
  * `kn`: Compute the Chern number of the plane perpendicular to the `"kn"` direction in Brillouin zone (`"k1"`, `"k2"`, `"k3"`).
  * `N1`: Number of mesh in `"kn"` direction.
  * `N2`: The number of points for one direction in the Brillouin zone.

# Returns

A `WCSProblem` object.

# Example

```julia
julia> 
```
