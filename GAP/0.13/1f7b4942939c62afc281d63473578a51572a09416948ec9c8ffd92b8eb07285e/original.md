```
setbangproperty!(x::GapObj, f::Union{AbstractString,Int64,Symbol}, v)
```

Set the value of the component `f` in the [component object](GAP_ref(ref:IsComponentObjectRep)) `x` to `v`, and return `x`.

# Examples

```jldoctest
julia> x = GAP.Globals.Iterator(GAP.Globals.Integers)
GAP: <iterator of Integers at 0>

julia> GAP.Globals.IsComponentObjectRep(x)
true

julia> setbangproperty!(x, :counter, 3)
GAP: <iterator of Integers at -1>

julia> getbangproperty(x, :counter)
3
```
