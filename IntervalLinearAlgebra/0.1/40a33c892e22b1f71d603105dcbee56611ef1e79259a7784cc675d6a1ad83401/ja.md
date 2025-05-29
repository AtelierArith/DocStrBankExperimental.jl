```
interval_norm(A::AbstractVector{T}) where {T<:Interval}
```

は区間ベクトル $v$ の無限大ノルムを計算します。

### 例

```jldoctest
julia> b = [-2..2, -3..2]
2-element Vector{Interval{Float64}}:
 [-2, 2]
 [-3, 2]

julia> interval_norm(b)
3.0
```
