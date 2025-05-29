```
cat_relevel(cat_array::CategoricalArray, levels_order::Vector{String}, after::Int=0)
```

Reorders the levels in a categorical array according to the provided order.

# Arguments

`cat_array`: Input categorical array. `levels_order`: Vector of levels in the desired order. `after`: Position after which to insert the new levels. Default is ignored

# Returns

Categorical array with levels reordered according to levels_order.

# Examples

```jldoctest
julia> cat_array = CategoricalArray(["A", "B", "C", "A", "B", "B"], ordered=true)
6-element CategoricalArrays.CategoricalArray{String,1,UInt32}:
 "A"
 "B"
 "C"
 "A"
 "B"
 "B"

julia> println(levels(cat_relevel(cat_array, ["B", "A", "C"])))
["B", "A", "C"]

julia> println(levels(cat_relevel(cat_array, ["A"], after=1)))
["B", "A", "C"]

julia> cat_array = CategoricalArray(["A", "B", "C", "A", "B", missing], ordered=true);

julia> println(levels(cat_relevel(cat_array, ["C", "A", "B", missing]), skipmissing=false))
Union{Missing, String}["C", "A", "B", missing]
```
