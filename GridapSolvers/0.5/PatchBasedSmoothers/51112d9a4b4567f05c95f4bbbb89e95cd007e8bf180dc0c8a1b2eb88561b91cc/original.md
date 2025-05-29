```
function PatchFESpace(
  space::Gridap.MultiField.MultiFieldFESpace,
  patch_decomposition::PatchDecomposition,
  cell_conformity::Vector{<:CellConformity};
  kwargs...
)
```

`PatchFESpace` constructor for `MultiFieldFESpace`.  Returns a `MultiFieldFESpace` of `PatchFESpace`s .
