`action(W::ComplexReflectionGroup,i::Integer,p::Perm)`

The elements of a `PermRootGroup` permute the roots of `parent(W)`, that is are  permutations on  `eachindex(roots(parent(W)))`. The  function `action` translates  this action of `p∈W` to `eachindex(roots(W))`. For a reflection subgroup we have `action(W,i,p)==restriction(W,inclusion(W,i)^p)` and for a parent  group `action(W,i,p)==i^p`. The first formula is always valid since for a parent group `restriction(W)==inclusion(W)==eachindex(roots(W))`.
