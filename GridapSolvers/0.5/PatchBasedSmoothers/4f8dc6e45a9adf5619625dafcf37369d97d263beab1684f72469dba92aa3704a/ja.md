```
function PatchFESpace(
  space::FESpaces.SingleFieldFESpace,
  patch_decomposition::PatchDecomposition,
  cell_conformity::CellConformity;
  patches_mask=Fill(false,num_patches(patch_decomposition))
)
```

グローバルな `SingleFieldFESpace`、`PatchDecomposition`、および `CellConformity` インスタンスから `PatchFESpace` を構築します。

`patches_mask[p] = true` の場合、パッチ `p` は無視されます。並列処理で使用されます。
