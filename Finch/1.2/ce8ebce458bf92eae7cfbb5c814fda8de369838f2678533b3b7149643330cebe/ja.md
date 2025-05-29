```
pattern!(fbr)
```

`fbr`のパターンを返します。つまり、`fbr`がそのfill_valueと構造的に異なる場所で真となるテンソルを返します。メモリを再利用し、変更時に元のテンソルを使用不可能にすることがあります。

```jldoctest
julia> A = Tensor(SparseList(Element(0.0), 10), [2.0, 0.0, 3.0, 0.0, 4.0, 0.0, 5.0, 0.0, 6.0, 0.0])
10 Tensor{SparseListLevel{Int64, Vector{Int64}, Vector{Int64}, ElementLevel{0.0, Float64, Int64, Vector{Float64}}}}:
 2.0
 0.0
 3.0
 0.0
 4.0
 0.0
 5.0
 0.0
 6.0
 0.0

julia> pattern!(A)
10 Tensor{SparseListLevel{Int64, Vector{Int64}, Vector{Int64}, PatternLevel{Int64}}}:
 1
 0
 1
 0
 1
 0
 1
 0
 1
 0
```
