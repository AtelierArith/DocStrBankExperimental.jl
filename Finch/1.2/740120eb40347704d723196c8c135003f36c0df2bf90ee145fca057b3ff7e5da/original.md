```
SparseIntervalLevel{[Ti=Int], [Left, Right]}(lvl, [dim])
```

The SparseIntervalLevel represent runs of equivalent slices `A[:, ..., :, i]` which are not entirely [`fill_value`](@ref). A main difference compared to SparseRunList level is that SparseInterval level only stores a 'single' non-fill run. It emits an error if the program tries to write multiple (>=2) runs into SparseInterval.

`Ti` is the type of the last tensor index. The types `Left`, and 'Right' are the types of the arrays used to store positions and endpoints.

```jldoctest
julia> tensor_tree(Tensor(SparseInterval(Element(0)), [0, 10, 0]))
3-Tensor
└─ SparseInterval (0) [1:3]
   └─ [2:2]: 10

julia> x = Tensor(SparseInterval(Element(0)), 10);

julia> @finch begin for i = extent(3,6); x[~i] = 1 end end;

julia> tensor_tree(x)
10-Tensor
└─ SparseInterval (0) [1:10]
   └─ [3:6]: 1

```
