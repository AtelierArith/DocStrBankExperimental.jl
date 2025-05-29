Prepare one or more Bell pairs (with optional phases).

```jldoctest
julia> bell()
+ XX
+ ZZ

julia> bell(2)
+ XX__
+ ZZ__
+ __XX
+ __ZZ

julia> bell((true, false))
- XX
+ ZZ

julia> bell([true, false, true, true])
- XX__
+ ZZ__
- __XX
- __ZZ
```
