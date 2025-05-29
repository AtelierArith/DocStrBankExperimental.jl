```
SCProblem(H, N, Nf)
```

Constructs a second Chern number problem with the default parameters.

# Arguments

  * `H`: The Hamiltonian function `H=H(k, p)` that defines the system. `k` is a abstract vector (or a tuple) of the wavenumber vector and `p` contains parameter. Dimension of `k` must be 4.
  * `N`: The number of points in the Brillouin zone. Type of `Int` means the uniform mesh. You can also specify the mesh by giving a tuple or a vector.
  * `Nf`: The number of filled bands. `nothing` means the half-filling.

# Returns

A `SCProblem` object.

# Example

```julia
julia> 
```
