```
MeshCell <: AbstractMeshCell
```

Single cell element in unstructured or polygonal grid.

It is characterised by a cell type (for instance, `VTKCellType.TRIANGLE` or `PolyData.Strips`) and by a connectivity vector determining the points on the grid defining this cell.

---

```
MeshCell(cell_type, connectivity)
```

Define a single cell element of an unstructured grid.

The `cell_type` argument characterises the type of cell (e.g. vertex, triangle, hexaedron, ...):

  * cell types for unstructured datasets are defined in the [`VTKCellTypes`](@ref)

module;

  * cell types for polygonal datasets are defined in the [`PolyData`](@ref) module.

The `connectivity` argument is a vector or tuple containing the indices of the points passed to `vtk_grid` which define this cell.

# Example

Define a triangular cell passing by points with indices `[3, 5, 42]`.

```jldoctest
julia> cell = MeshCell(VTKCellTypes.VTK_TRIANGLE, (3, 5, 42))
MeshCell{VTKCellType, Tuple{Int64, Int64, Int64}}(VTKCellType("VTK_TRIANGLE", 0x05, 3), (3, 5, 42))
```
