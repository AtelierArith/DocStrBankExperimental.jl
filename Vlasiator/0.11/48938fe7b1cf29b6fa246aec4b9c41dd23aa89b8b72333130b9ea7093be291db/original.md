```
write_vtk(meta::MetaVLSV; kwargs...)
write_vtk(file::AbstractString; kwargs...)
```

Convert VLSV file to VTK format.

# Keywords

  * `vars::Vector{String}=[""]`: select which variables to convert.
  * `ascii::Bool=false`: output stored in ASCII or compressed binary format.
  * `maxamronly::Bool=false`: generate image files on the highest refinement level only.
  * `box::Vector`: selected box range in 3D.
  * `outdir::String=""`: output directory.
  * `verbose::Bool=false`: display logs during conversion.
