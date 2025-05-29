`inclusion(W::ComplexReflectionGroup)`

the indices of the roots of `W` in the roots of `parent(W)`.

`inclusion(W::PermRootGroup,i::Integer)` `inclusion(W::PermRootGroup,v::AbstractVector{<:Integer})`

same as `inclusion(W)[i]` or `inclusion(W)[v]` (but more efficient).
