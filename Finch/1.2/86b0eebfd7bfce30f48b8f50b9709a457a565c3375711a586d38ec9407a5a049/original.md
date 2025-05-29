```
RunListLevel{[Ti=Int], [Ptr, Right]}(lvl, [dim], [merge = true])
```

The RunListLevel represent runs of equivalent slices `A[:, ..., :, i]`. A sorted list is used to record the right endpoint of each run. Optionally, `dim` is the size of the last dimension.

`Ti` is the type of the last tensor index, and `Tp` is the type used for positions in the level. The types `Ptr` and `Right` are the types of the arrays used to store positions and endpoints.

The `merge` keyword argument is used to specify whether the level should merge duplicate consecutive runs.

```jldoctest
julia> tensor_tree(Tensor(Dense(RunListLevel(Element(0.0))), [10 0 20; 30 0 0; 0 0 40]))
3×3-Tensor
└─ Dense [:,1:3]
   ├─ [:, 1]: RunList (0.0) [1:3]
   │  ├─ [1:1]: 10.0
   │  ├─ [2:2]: 30.0
   │  └─ [3:3]: 0.0
   ├─ [:, 2]: RunList (0.0) [1:3]
   │  └─ [1:3]: 0.0
   └─ [:, 3]: RunList (0.0) [1:3]
      ├─ [1:1]: 20.0
      ├─ [2:2]: 0.0
      └─ [3:3]: 40.0
```
