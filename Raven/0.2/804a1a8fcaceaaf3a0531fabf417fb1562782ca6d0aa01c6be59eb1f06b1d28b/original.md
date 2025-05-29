```
GridArray{T}(undef, grid::Grid)
```

Create an array containing elements of type `T` for each point in the grid (including the ghost cells).  The dimensions of the array is `(size(referencecell(grid))..., length(grid))` as the ghost cells are hidden by default.

The type `T` is assumed to be able to be interpreted into an `NTuple{M,L}`. Some example types (some using `StructArrays`) are:

  * `T = NamedTuple{(:E,:B),Tuple{SVector{3,ComplexF64},SVector{3,ComplexF64}}}`
  * `T = NTuple{5,Int64}`
  * `T = SVector{5,Int64}`
  * `T = ComplexF32`
  * `T = Float32`

Instead of using an array-of-struct style storage, a GPU efficient struct-of-arrays like storage is used.  For example, instead of storing data like

```julia-repl
julia> T = Tuple{Int,Int};
julia> data = Array{T}(undef, 3, 4, 2); a .= Ref((1,2))
3×4 Matrix{Tuple{Int64, Int64}}:
 (1, 2)  (1, 2)  (1, 2)  (1, 2)
 (1, 2)  (1, 2)  (1, 2)  (1, 2)
 (1, 2)  (1, 2)  (1, 2)  (1, 2)
```

the data would be stored in the order

```julia-repl
julia> permutedims(reinterpret(reshape, Int, data), (2,3,1,4))
3×4×2×2 Array{Int64, 4}:
[:, :, 1, 1] =
 1  1  1  1
 1  1  1  1
 1  1  1  1

[:, :, 2, 1] =
 2  2  2  2
 2  2  2  2
 2  2  2  2

[:, :, 1, 2] =
 1  1  1  1
 1  1  1  1
 1  1  1  1

[:, :, 2, 2] =
 2  2  2  2
 2  2  2  2
 2  2  2  2
```

For a `GridArray` the indices before the ones associated with `T` (the first two in the example above) are associated with the degrees-of-freedoms of the cells.  The one after is associated with the number of cells.
