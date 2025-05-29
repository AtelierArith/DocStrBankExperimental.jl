```
function PatchDecomposition(
  model::DiscreteModel{Dc,Dp};
  Dr=0,
  patch_boundary_style::PatchBoundaryStyle=PatchBoundaryExclude(),
  boundary_tag_names::AbstractArray{String}=["boundary"]
)
```

Returns an instance of [`PatchDecomposition`](@ref) from a given discrete model.
