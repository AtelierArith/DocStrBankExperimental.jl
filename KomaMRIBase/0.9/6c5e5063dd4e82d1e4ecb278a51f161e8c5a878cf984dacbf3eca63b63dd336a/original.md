```
obj = brain_phantom3D(; ss=4, us=1, start_end=[160,200])
```

Creates a three-dimentional brain Phantom struct. Default ss=4 sample spacing is 2 mm. Original file (ss=1) sample spacing is .5 mm. 

# References

  * B. Aubert-Broche, D.L. Collins, A.C. Evans: "A new improved version of the realistic   digital brain phantom" NeuroImage, in review - 2006
  * B. Aubert-Broche, M. Griffin, G.B. Pike, A.C. Evans and D.L. Collins: "20 new digital   brain phantoms for creation of validation image data bases" IEEE TMI, in review - 2006
  * https://brainweb.bic.mni.mcgill.ca/brainweb/tissue*mr*parameters.txt

# Keywords

  * `ss`: (`::Integer or ::Vector{Integer}`, `=4`) subsampling parameter for all axes if scaler, per axis if 3 element vector [ssx, ssy, ssz]
  * `us`: (`::Integer or ::Vector{Integer}`, `=1`)  upsampling parameter for all axes if scaler, per axis if 3 element vector [usx, usy, usz]
  * `start_end`: (`::Vector{Integer}`, `=[160,200]`) z index range of presampled phantom, 180 is center

# Returns

  * `obj`: (`::Phantom`) 3D Phantom struct

# Examples

```julia-repl
julia> obj = brain_phantom3D(; ss=5)

julia> obj = brain_phantom3D(; us=[2, 2, 1])

julia> plot_phantom_map(obj, :ρ)
```
