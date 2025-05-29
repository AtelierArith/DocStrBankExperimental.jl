```
DenseLevel{[Ti=Int]}(lvl, [dim])
```

A subfiber of a dense level is an array which stores every slice `A[:, ..., :, i]` as a distinct subfiber in `lvl`. Optionally, `dim` is the size of the last dimension. `Ti` is the type of the indices used to index the level.

```jldoctest
julia> ndims(Tensor(Dense(Element(0.0))))
1

julia> ndims(Tensor(Dense(Dense(Element(0.0)))))
2

julia> tensor_tree(Tensor(Dense(Dense(Element(0.0))), [1 2; 3 4]))
2×2-Tensor
└─ Dense [:,1:2]
   ├─ [:, 1]: Dense [1:2]
   │  ├─ [1]: 1.0
   │  └─ [2]: 3.0
   └─ [:, 2]: Dense [1:2]
      ├─ [1]: 2.0
      └─ [2]: 4.0
```
