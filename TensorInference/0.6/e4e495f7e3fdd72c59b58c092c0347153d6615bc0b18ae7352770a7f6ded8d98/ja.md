```julia
struct BeliefPropgation{T}
```

```
BeliefPropgation(nvars::Int, t2v::AbstractVector{Vector{Int}}, tensors::AbstractVector{AbstractArray{T}}) where T
```

信念伝播オブジェクト。

### フィールド

  * `t2v::Vector{Vector{Int}}`: テンソルから変数へのマッピング
  * `v2t::Vector{Vector{Int}}`: 変数からテンソルへのマッピング
  * `tensors::Vector{AbstractArray{T}}`: テンソル
