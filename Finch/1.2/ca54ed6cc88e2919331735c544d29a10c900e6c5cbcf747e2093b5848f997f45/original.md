```
SparsePointLevel{[Ti=Int], [Idx]}(lvl, [dim])
```

A subfiber of a SparsePoint level does not need to represent slices `A[:, ..., :, i]` which are entirely [`fill_value`](@ref). Instead, only potentially non-fill slices are stored as subfibers in `lvl`. A main difference compared to SparseList level is that SparsePoint level only stores a 'single' non-fill slice. It emits an error if the program tries to write multiple (>=2) coordinates into SparsePoint.

`Ti` is the type of the last tensor index. The types `Ptr` and `Idx` are the types of the arrays used to store positions and indicies.

```jldoctest
julia> tensor_tree(Tensor(Dense(SparsePoint(Element(0.0))), [10 0 0; 0 20 0; 0 0 30]))
3×3-Tensor
└─ Dense [:,1:3]
   ├─ [:, 1]: SparsePoint (0.0) [1:3]
   │  └─ [1]: 10.0
   ├─ [:, 2]: SparsePoint (0.0) [1:3]
   │  └─ [2]: 20.0
   └─ [:, 3]: SparsePoint (0.0) [1:3]
      └─ [3]: 30.0

julia> tensor_tree(Tensor(SparsePoint(Dense(Element(0.0))), [0 0 0; 0 0 30; 0 0 30]))
3×3-Tensor
└─ SparsePoint (0.0) [:,1:3]
   └─ [:, 3]: Dense [1:3]
      ├─ [1]: 0.0
      ├─ [2]: 30.0
      └─ [3]: 30.0

```
