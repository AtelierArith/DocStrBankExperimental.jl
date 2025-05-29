SparseBandLevel{[Ti=Int], [Idx, Ofs]}(lvl, [dim])

[`SparseBlockListLevel`](@ref)と同様ですが、単一のブロックのみを格納し、ゼロで埋めます。

```jldoctest julia> Tensor(Dense(SparseBand(Element(0.0))), [10 0 20; 30 40 0; 0 0 50]) Dense [:,1:3] ├─[:,1]: SparseList (0.0) [1:3] │ ├─[1]: 10.0 │ ├─[2]: 30.0 ├─[:,2]: SparseList (0.0) [1:3] ├─[:,3]: SparseList (0.0) [1:3] │ ├─[1]: 20.0 │ ├─[3]: 40.0

```
