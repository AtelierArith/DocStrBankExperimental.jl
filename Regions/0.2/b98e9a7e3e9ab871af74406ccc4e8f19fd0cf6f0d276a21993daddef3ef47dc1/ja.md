```
contains(x::UnitRange{Int64}, y::Integer)
```

範囲 x が値 x を含むかどうかをテストします。

contains メソッドに加えて、∈ 演算子も使用できます。

```jldoctest
julia> using Regions

julia> contains(0:10, 5)
true

julia> contains(0:10, 15)
false

julia> 0 ∈ 0:10
true

julia> 100 ∈ 0:10
false
```
