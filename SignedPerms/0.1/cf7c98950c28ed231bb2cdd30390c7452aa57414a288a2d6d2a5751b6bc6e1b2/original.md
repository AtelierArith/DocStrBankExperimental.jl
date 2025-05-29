SPerm{T}(x::Integer...)where T<:Integer

returns as a `SPerm{T}` a signed cycle. For instance `SPerm{Int8}(1,-2,-1,2)`  and `SPerm({Int8}[-2,1])` define  the same signed permutation. If not given `{T}` is taken to be `{Int16}`.
