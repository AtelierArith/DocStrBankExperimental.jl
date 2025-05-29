```
function PatchFESpace(
  space::FESpaces.SingleFieldFESpace,
  patch_decomposition::PatchDecomposition,
  cell_conformity::CellConformity;
  patches_mask=Fill(false,num_patches(patch_decomposition))
)
```

Constructs a `PatchFESpace` from a global `SingleFieldFESpace`, a `PatchDecomposition` and a `CellConformity` instance.

If `patches_mask[p] = true`, the patch `p` is ignored. Used in parallel.
