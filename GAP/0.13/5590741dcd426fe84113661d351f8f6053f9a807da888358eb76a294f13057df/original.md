```
getbangindex(x::GapObj, i::Int64)
```

Return the entry at position `i` in the [positional object](GAP_ref(ref:IsPositionalObjectRep)) `x`.

# Examples

```jldoctest
julia> x = GAP.Globals.ZmodnZObj(1, 6)
GAP: ZmodnZObj( 1, 6 )

julia> GAP.Globals.IsPositionalObjectRep(x)
true

julia> getbangindex(x, 1)
1
```
