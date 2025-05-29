```
obj = pelvis_phantom2D(; ss=4, us=1)
```

Creates a two-dimensional pelvis Phantom struct. Default ss=4 sample spacing is 2 mm. Original file (ss=1) sample spacing is .5 mm.

# Keywords

  * `ss`: (`::Integer or ::Vector{Integer}`, `=4`) subsampling parameter for all axes if scaler, per axis if 2 element vector [ssx, ssy]
  * `us`: (`::Integer or ::Vector{Integer}`, `=1`)  upsampling parameter for all axes if scaler, per axis if 2 element vector [usx, usy]

# Returns

  * `obj`: (`::Phantom`) Phantom struct

# Examples

```julia-repl
julia> obj = pelvis_phantom2D(; ss=2])

julia> obj = pelvis_phantom2D(; us=[1, 2])

julia> pelvis_phantom2D(obj, :ρ)
```
