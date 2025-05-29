```
translate = Translate(dx, dy, dz)
```

Translate struct. It produces a linear translation. Its fields are the final displacements in the three axes (dx, dy, dz).

# Arguments

  * `dx`: (`::Real`, `[m]`) translation in x
  * `dy`: (`::Real`, `[m]`) translation in y
  * `dz`: (`::Real`, `[m]`) translation in z

# Returns

  * `translate`: (`::Translate`) Translate struct

# Examples

```julia-repl
julia> translate = Translate(dx=0.01, dy=0.02, dz=0.03)
```
