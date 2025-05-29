```
pixwin(nside; pol=false)
```

# Arguments:

  * `nside`: HEALPix resolution parameter

# Keywords

  * `pol::Bool=false`: if true, also return polarization pixel window

# Returns:

  * `Vector{Float64}` pixel window function. If `pol=true`, returns a Tuple   of the temperature and polarization pixel windows.

# Examples

```julia-repl
julia> pixwin(4)
17-element Vector{Float64}:
 1.0000000000020606
 0.9942340766588788
 ⋮
 0.4222841034207188
```
