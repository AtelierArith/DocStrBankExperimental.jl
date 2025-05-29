```
load_procar(filename::String="PROCAR"; spin::Bool=false, noncollinear::Bool=false) -> Projection, KPoints, Bands
```

Load projection of wave function ⟨Yₗₘ|ϕₙₖ⟩ from PROCAR file.

# Arguments

  * `filename::String="PROCAR"`: name of input file
  * `spin::Bool=false`: ISPIN = 0(false) or 1(true)
  * `noncollinear::Bool=false`: LNONCOLINEAR = 0(false) or 1(true). For noncolinear=1, value of spin is neglected.

# Returns for collinear

  * `Projection`: Projection of wave function ⟨Yₗₘ|ϕₙₖ⟩
  * `Array{KPoint, 1}`: metadata of k-points
  * `Bands`: metadata of all bands

# Returns for noncollinear

  * `Projection`: Total projection of wave function ⟨Yₗₘ|ϕₙₖ⟩
  * `Projection`: Projection of spin along x-axis
  * `Projection`: Projection of spin along y-axis
  * `Projection`: Projection of spin along z-axis
  * `Array{KPoint, 1}`: metadata of k-points
  * `Bands`: metadata of all bands
