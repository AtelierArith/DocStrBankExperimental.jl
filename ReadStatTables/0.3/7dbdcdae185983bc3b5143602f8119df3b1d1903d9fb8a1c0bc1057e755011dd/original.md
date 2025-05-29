```
LabeledValue{T, K}
```

Value of type `T` associated with a dictionary of value labels with keys of type `K`. If a value `v` is not euqal (`==`) to a key in the dictionary, then `string(v)` is taken as the value label. See also [`LabeledArray`](@ref).

The value underlying a `LabeledValue` can be accessed via [`unwrap`](@ref). The value label can be obtained by calling [`valuelabel`](@ref) or converting a `LabeledValue` to `String` via `convert`. The dictionary of value labels (typically assoicated with a data column) can be accessed via [`getvaluelabels`](@ref).

Comparison operators `==`, `isequal`, `<`, `isless` and `isapprox` compare the underlying value of type `T` and disregard any value label. To compare the value label, use [`valuelabel`](@ref) to retrieve the label first.

# Examples

```jldoctest
julia> lbls = Dict{Int,String}(0=>"a", 1=>"a");

julia> v0 = LabeledValue(0, lbls)
0 => a

julia> v1 = LabeledValue(1, lbls)
1 => a

julia> vm = LabeledValue(missing, lbls)
missing => missing

julia> v0 == v1
false

julia> v1 == 1
true

julia> isnan(v1)
false

julia> isequal(vm, missing)
true

julia> unwrap(v0)
0

julia> valuelabel(v1) == "a"
true

julia> getvaluelabels(v1) === lbls
true
```
