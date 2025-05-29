```
SparseListLevel{[Ti=Int], [Ptr, Idx]}(lvl, [dim])
```

A subfiber of a sparse level does not need to represent slices `A[:, ..., :, i]` which are entirely [`fill_value`](@ref). Instead, only potentially non-fill slices are stored as subfibers in `lvl`.  A sorted list is used to record which slices are stored. Optionally, `dim` is the size of the last dimension.

`Ti` is the type of the last tensor index, and `Tp` is the type used for positions in the level. The types `Ptr` and `Idx` are the types of the arrays used to store positions and indicies.

```jldoctest
julia> tensor_tree(Tensor(Dense(SparseList(Element(0.0))), [10 0 20; 30 0 0; 0 0 40]))
3×3-Tensor
└─ Dense [:,1:3]
   ├─ [:, 1]: SparseList (0.0) [1:3]
   │  ├─ [1]: 10.0
   │  └─ [2]: 30.0
   ├─ [:, 2]: SparseList (0.0) [1:3]
   └─ [:, 3]: SparseList (0.0) [1:3]
      ├─ [1]: 20.0
      └─ [3]: 40.0

julia> tensor_tree(Tensor(SparseList(SparseList(Element(0.0))), [10 0 20; 30 0 0; 0 0 40]))
3×3-Tensor
└─ SparseList (0.0) [:,1:3]
   ├─ [:, 1]: SparseList (0.0) [1:3]
   │  ├─ [1]: 10.0
   │  └─ [2]: 30.0
   └─ [:, 3]: SparseList (0.0) [1:3]
      ├─ [1]: 20.0
      └─ [3]: 40.0

```
