```julia
unionize(x::AbstractVector)
```

抽象要素型を持つ配列を、配列内のすべての要素の型のUnionを持つ `eltype` を持つ配列に変換します。

常にコピーを返します。たとえ `x` がすでにユニオン化されていてもです。

### 例

```julia
julia> a = Any[false, 0, 1.0]
3-element Vector{Any}:
 false
     0
     1.0

julia> unionize(a)
3-element Vector{Union{Bool, Float64, Int64}}:
 false
     0
     1.0
```
