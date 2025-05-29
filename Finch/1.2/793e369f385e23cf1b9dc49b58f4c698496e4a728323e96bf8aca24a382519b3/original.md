SparseBlockListLevel{[Ti=Int], [Ptr, Idx, Ofs]}(lvl, [dim])

Like the [`SparseListLevel`](@ref), but contiguous subfibers are stored together in blocks.

```jldoctest julia> Tensor(Dense(SparseBlockList(Element(0.0))), [10 0 20; 30 0 0; 0 0 40]) Dense [:,1:3] ├─[:,1]: SparseList (0.0) [1:3] │ ├─[1]: 10.0 │ ├─[2]: 30.0 ├─[:,2]: SparseList (0.0) [1:3] ├─[:,3]: SparseList (0.0) [1:3] │ ├─[1]: 20.0 │ ├─[3]: 40.0

julia> Tensor(SparseBlockList(SparseBlockList(Element(0.0))), [10 0 20; 30 0 0; 0 0 40]) SparseList (0.0) [:,1:3] ├─[:,1]: SparseList (0.0) [1:3] │ ├─[1]: 10.0 │ ├─[2]: 30.0 ├─[:,3]: SparseList (0.0) [1:3] │ ├─[1]: 20.0 │ ├─[3]: 40.0
