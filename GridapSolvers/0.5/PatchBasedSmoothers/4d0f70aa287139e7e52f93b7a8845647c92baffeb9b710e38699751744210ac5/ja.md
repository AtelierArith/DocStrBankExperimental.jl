```
function PatchDecomposition(
  model::DiscreteModel{Dc,Dp};
  Dr=0,
  patch_boundary_style::PatchBoundaryStyle=PatchBoundaryExclude(),
  boundary_tag_names::AbstractArray{String}=["boundary"]
)
```

与えられた離散モデルから[`PatchDecomposition`](@ref)のインスタンスを返します。
