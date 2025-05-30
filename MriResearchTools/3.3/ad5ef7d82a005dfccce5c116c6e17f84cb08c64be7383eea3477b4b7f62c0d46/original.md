```
header(v::NIVolume)
```

Returns a copy of the header with the orientation information.

# Examples

```julia-repl
julia> vol = readmag("image.nii")
julia> hdr = header(vol)
julia> savenii(vol .+ 10, "vol10.nii"; header=hdr)
```
