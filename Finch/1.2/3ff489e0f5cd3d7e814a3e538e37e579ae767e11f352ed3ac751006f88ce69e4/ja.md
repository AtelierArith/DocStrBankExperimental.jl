```
set_fill_value!(fbr, init)
```

`fbr` と等しいテンソルを返しますが、フィル（暗黙の）値が `init` に設定されています。メモリを再利用し、変更時に元のテンソルを使用不可能にすることがあります。

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

julia> set_fill_value!(A, Inf)
10 Tensor{SparseListLevel{Int64, Vector{Int64}, Vector{Int64}, ElementLevel{Inf, Float64, Int64, Vector{Float64}}}}:
  2.0
 Inf
  3.0
 Inf
  4.0
 Inf
  5.0
 Inf
  6.0
 Inf
```
