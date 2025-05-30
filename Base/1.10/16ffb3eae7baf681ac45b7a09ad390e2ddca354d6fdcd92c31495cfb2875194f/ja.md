```
NaN, NaN64
```

型 [`Float64`](@ref) の非数値（not-a-number）値。

参照: [`isnan`](@ref), [`missing`](@ref), [`NaN32`](@ref), [`Inf`](@ref).

# 例

```jldoctest
julia> 0/0
NaN

julia> Inf - Inf
NaN

julia> NaN == NaN, isequal(NaN, NaN), NaN === NaN
(false, true, true)
```
