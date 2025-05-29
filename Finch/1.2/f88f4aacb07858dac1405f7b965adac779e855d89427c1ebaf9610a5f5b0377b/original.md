SparseBandLevel{[Ti=Int], [Idx, Ofs]}(lvl, [dim])

Like the [`SparseBlockListLevel`](@ref), but stores only a single block, and fills in zeros.

```jldoctest julia> Tensor(Dense(SparseBand(Element(0.0))), [10 0 20; 30 40 0; 0 0 50]) Dense [:,1:3] ├─[:,1]: SparseList (0.0) [1:3] │ ├─[1]: 10.0 │ ├─[2]: 30.0 ├─[:,2]: SparseList (0.0) [1:3] ├─[:,3]: SparseList (0.0) [1:3] │ ├─[1]: 20.0 │ ├─[3]: 40.0
