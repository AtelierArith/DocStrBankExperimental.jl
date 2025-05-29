```
setbangindex!(x::GapObj, v::Any, i::Int64)
```

Set the entry at position `i` in the [positional object](GAP_ref(ref:IsPositionalObjectRep)) `x` to `v`, and return `x`.

# Examples

```jldoctest
julia> x = GAP.Globals.ZmodnZObj(1, 6)
GAP: ZmodnZObj( 1, 6 )

julia> GAP.Globals.IsPositionalObjectRep(x)
true

julia> setbangindex!(x, 0, 1)
GAP: ZmodnZObj( 0, 6 )
```
