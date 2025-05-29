SparseBlockListLevel{[Ti=Int], [Ptr, Idx, Ofs]}(lvl, [dim])

[`SparseListLevel`](@ref)と同様ですが、連続したサブファイバーがブロックとして一緒に保存されます。

```jldoctest julia> Tensor(Dense(SparseBlockList(Element(0.0))), [10 0 20; 30 0 0; 0 0 40]) Dense [:,1:3] ├─[:,1]: SparseList (0.0) [1:3] │ ├─[1]: 10.0 │ ├─[2]: 30.0 ├─[:,2]: SparseList (0.0) [1:3] ├─[:,3]: SparseList (0.0) [1:3] │ ├─[1]: 20.0 │ ├─[3]: 40.0

julia> Tensor(SparseBlockList(SparseBlockList(Element(0.0))), [10 0 20; 30 0 0; 0 0 40]) SparseList (0.0) [:,1:3] ├─[:,1]: SparseList (0.0) [1:3] │ ├─[1]: 10.0 │ ├─[2]: 30.0 ├─[:,3]: SparseList (0.0) [1:3] │ ├─[1]: 20.0 │ ├─[3]: 40.0
