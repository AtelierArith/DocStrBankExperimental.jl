```
is_abelian(ops::AbstractVector{SymOperation}, [cntr::Union{Char, Nothing}])  -->  Bool
```

Return the whether the group composed of the elements `ops` is Abelian.

A group $G$ is Abelian if all its elements commute mutually, i.e., if $g = hgh^{-1}$ for all $g,h ∈ G$.

See discussion of the setting argument `cntr` in [`classes`](@ref).
