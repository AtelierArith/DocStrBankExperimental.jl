`restriction(W::PermRootGroup)`

A  list for each root of `parent(W)`, which  holds `0` if the root is not a root of `W` and `i` if the root is the `i`-th root of `W`.

`restriction(W::PermRootGroup,i::Integer)` `restriction(W::PermRootGroup,v::AbstractVector{<:Integer})`

same as `restriction(W)[i]` or `restriction(W)[v]` (but more efficient).
