```
phantom = brain_phantom2D(;axis="axial", ss=4)
```

Creates a two-dimensional brain Phantom struct. Default ss=4 sample spacing is 2 mm. Original file (ss=1) sample spacing is .5 mm.

# References

  * B. Aubert-Broche, D.L. Collins, A.C. Evans: "A new improved version of the realistic   digital brain phantom" NeuroImage, in review - 2006
  * B. Aubert-Broche, M. Griffin, G.B. Pike, A.C. Evans and D.L. Collins: "20 new digital   brain phantoms for creation of validation image data bases" IEEE TMI, in review - 2006
  * https://brainweb.bic.mni.mcgill.ca/brainweb/tissue*mr*parameters.txt

# Keywords

  * `axis`: (`::String`, `="axial"`, opts=[`"axial"`, `"coronal"`, `"sagittal"`]) orientation of the phantom
  * `ss`: (`::Integer or ::Vector{Integer}`, `=4`) subsampling parameter for all axes if scaler, per axis if 2 element vector [ssx, ssy]
  * `us`: (`::Integer or ::Vector{Integer}`, `=1`)  upsampling parameter for all axes if scaler, per axis if 2 element vector [usx, usy], if used ss is set to ss=1

# Returns

  * `obj`: (`::Phantom`) Phantom struct

# Examples

```julia-repl
julia> obj = brain_phantom2D(; axis="sagittal", ss=1)

julia> obj = brain_phantom2D(; axis="axial", us=[1, 2])

julia> plot_phantom_map(obj, :ρ)
```
