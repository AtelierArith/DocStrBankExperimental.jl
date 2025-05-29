```
conventionalize(V′::Union{AbstractBasis, AbstractPoint}, 
                cntr_or_sgnum::Union{Char, <:Integer})    -->  V::typeof(V′)
```

Return the conventional basis or point `V` associated with the input primitive `AbstractBasis` or `AbstractPoint` `V′`.

The assumed centering type is specified by `cntr_or_sgnum`, given either as a centering character (`::Char`) or inferred from a space group number (`::Integer`) and the dimensionality of `V′` (see also [`centering(::Integer, ::Integer)`](@ref)).
