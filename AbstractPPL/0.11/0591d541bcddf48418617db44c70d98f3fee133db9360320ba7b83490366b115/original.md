```
varname_to_string(vn::VarName)
```

Convert a `VarName` as a string, via an intermediate dictionary. This differs from `string(vn)` in that concretised slices are faithfully represented (rather than being pretty-printed as colons).

For `VarName`s which index into an array, this function will only work if the indices can be serialised. This is true for all standard Julia index types, but if you are using custom index types, you will need to implement the `index_to_dict` and `dict_to_index` methods for those types. See the documentation of [`dict_to_index`](@ref) for instructions on how to do this.

```jldoctest
julia> varname_to_string(@varname(x))
"{\"optic\":{\"type\":\"identity\"},\"sym\":\"x\"}"

julia> varname_to_string(@varname(x.a))
"{\"optic\":{\"field\":\"a\",\"type\":\"property\"},\"sym\":\"x\"}"

julia> y = ones(2); varname_to_string(@varname(y[:]))
"{\"optic\":{\"indices\":{\"values\":[{\"type\":\"Base.Colon\"}],\"type\":\"Base.Tuple\"},\"type\":\"index\"},\"sym\":\"y\"}"

julia> y = ones(2); varname_to_string(@varname(y[:], true))
"{\"optic\":{\"indices\":{\"values\":[{\"range\":{\"stop\":2,\"type\":\"Base.OneTo\"},\"type\":\"AbstractPPL.ConcretizedSlice\"}],\"type\":\"Base.Tuple\"},\"type\":\"index\"},\"sym\":\"y\"}"
```
