```
magnitude(headmodel::AbstractHeadmodel)
```

Return the magnitude for the given `headmodel` based on the leadfield (and potentially the source orientations) specified in the `headmodel`.

If the `headmodel` includes source orientations these are used in the calculations, otherwise the `leadfield` is returned assuming that the source orientations are already included. Please note that (at least in the case of the HArtMuT model) the leadfield for the cortical sources is used.

# Returns

  * `Matrix{Float64}`: Contribution of each source to the potential measured at each electrode taking into account the orientation of the sources.   The output dimensions are `electrodes x sources`.

# Examples

```julia-repl
# Using the HArtMut model as an example
julia> h = Hartmut();
Please cite: HArtMuT: Harmening Nils, Klug Marius, Gramann Klaus and Miklody Daniel - 10.1088/1741-2552/aca8ce

julia> magnitude(h)
227×2004 Matrix{Float64}:
  0.111706   …   0.301065
  0.0774359      0.332934
  ⋮          ⋱  
 -0.164539      -0.246555
```
