```
contains(x::UnitRange{Int64}, y::Integer)
```

Test if range x contains value x.

In addition to the contains method, you can also use the ∈ operator.

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
