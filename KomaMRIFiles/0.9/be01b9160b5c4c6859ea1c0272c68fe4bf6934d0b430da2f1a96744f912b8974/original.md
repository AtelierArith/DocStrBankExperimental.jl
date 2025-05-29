```
obj = read_phantom_jemris(filename)
```

Returns the Phantom struct from a JEMRIS phantom file `.h5`.

# Arguments

  * `filename`: (`::String`) the absolute or relative path of the phantom file `.h5`

# Returns

  * `obj`: (`::Phantom`) Phantom struct

# Examples

```julia-repl
julia> obj_file = joinpath(dirname(pathof(KomaMRI)), "../examples/2.phantoms/brain.h5")

julia> obj = read_phantom_jemris(obj_file)

julia> plot_phantom_map(obj, :ρ)
```
