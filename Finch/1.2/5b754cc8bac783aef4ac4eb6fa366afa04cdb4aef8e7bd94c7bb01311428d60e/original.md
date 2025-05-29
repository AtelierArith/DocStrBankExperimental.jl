```
SparseCOOLevel{[N], [TI=Tuple{Int...}], [Ptr, Tbl]}(lvl, [dims])
```

A subfiber of a sparse level does not need to represent slices which are entirely [`fill_value`](@ref). Instead, only potentially non-fill slices are stored as subfibers in `lvl`. The sparse coo level corresponds to `N` indices in the subfiber, so fibers in the sublevel are the slices `A[:, ..., :, i_1, ..., i_n]`.  A set of `N` lists (one for each index) are used to record which slices are stored. The coordinates (sets of `N` indices) are sorted in column major order.  Optionally, `dims` are the sizes of the last dimensions.

`TI` is the type of the last `N` tensor indices, and `Tp` is the type used for positions in the level.

The type `Tbl` is an NTuple type where each entry k is a subtype `AbstractVector{TI[k]}`.

The type `Ptr` is the type for the pointer array.

```jldoctest
julia> tensor_tree(Tensor(Dense(SparseCOO{1}(Element(0.0))), [10 0 20; 30 0 0; 0 0 40]))
3×3-Tensor
└─ Dense [:,1:3]
   ├─ [:, 1]: SparseCOO{1} (0.0) [1:3]
   │  ├─ [1]: 10.0
   │  └─ [2]: 30.0
   ├─ [:, 2]: SparseCOO{1} (0.0) [1:3]
   └─ [:, 3]: SparseCOO{1} (0.0) [1:3]
      ├─ [1]: 20.0
      └─ [3]: 40.0

julia> tensor_tree(Tensor(SparseCOO{2}(Element(0.0)), [10 0 20; 30 0 0; 0 0 40]))
3×3-Tensor
└─ SparseCOO{2} (0.0) [:,1:3]
   ├─ [1, 1]: 10.0
   ├─ [2, 1]: 30.0
   ├─ [1, 3]: 20.0
   └─ [3, 3]: 40.0
```
