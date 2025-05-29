```
Z2Problem(H, Nf, N)
```

Constructs a Z2 number problem with the default parameters.

# Arguments

  * `H`: The Hamiltonian function `H=H(k, p)` that defines the system. `k` is a abstract vector (or a tuple) of the wavenumber vector and `p` contains parameter. Dimension of `k` must be 2.
  * `Nf`: The number of filled bands. `nothing` means the half-filling.
  * `N`: The number of points for one direction in the Brillouin zone.

# Returns

A `Z2Problem` object.

# Example

```julia
julia> 
```
