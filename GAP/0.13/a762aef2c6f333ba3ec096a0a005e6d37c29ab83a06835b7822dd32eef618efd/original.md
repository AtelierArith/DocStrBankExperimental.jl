```
hasbangproperty(x::GapObj, f::Union{AbstractString,Int64,Symbol})
```

Return whether the [component object](GAP_ref(ref:IsComponentObjectRep)) `x` has the component `f`.

# Examples

```jldoctest
julia> x = GAP.Globals.Iterator(GAP.Globals.Integers)
GAP: <iterator of Integers at 0>

julia> GAP.Globals.IsComponentObjectRep(x)
true

julia> hasbangproperty(x, :counter)
true

julia> hasbangproperty(x, :x)
false
```
