```
hasbangindex(x::GapObj, i::Int64)
```

Return whether the entry at position `i` exists in the [positional object](GAP_ref(ref:IsPositionalObjectRep)) `x`.

# Examples

```jldoctest
julia> x = GAP.Globals.ZmodnZObj(1, 6)
GAP: ZmodnZObj( 1, 6 )

julia> GAP.Globals.IsPositionalObjectRep(x)
true

julia> hasbangindex(x, 1)
true

julia> hasbangindex(x, 2)
false
```
