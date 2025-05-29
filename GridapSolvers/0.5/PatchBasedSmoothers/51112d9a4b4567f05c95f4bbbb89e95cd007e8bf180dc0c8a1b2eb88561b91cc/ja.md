```
function PatchFESpace(
  space::Gridap.MultiField.MultiFieldFESpace,
  patch_decomposition::PatchDecomposition,
  cell_conformity::Vector{<:CellConformity};
  kwargs...
)
```

`PatchFESpace` コンストラクタは `MultiFieldFESpace` 用です。 `PatchFESpace` の `MultiFieldFESpace` を返します。
