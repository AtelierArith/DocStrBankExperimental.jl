```
getbangproperty(x::GapObj, f::Union{AbstractString,Int64,Symbol})
```

Return the value of the component `f` in the [component object](GAP_ref(ref:IsComponentObjectRep)) `x`.

# Examples

```jldoctest
julia> x = GAP.Globals.Iterator(GAP.Globals.Integers)
GAP: <iterator of Integers at 0>

julia> GAP.Globals.IsComponentObjectRep(x)
true

julia> getbangproperty(x, :counter)
0
```
