```
cat_rev(cat_array)
```

Reverses the order of levels in a categorical array.

# Arguments

`cat_array`: Input categorical array.

# Returns

Categorical array with reversed order of levels.

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

julia> cat_rev(cat_array)
6-element CategoricalArrays.CategoricalArray{String,1,UInt32}:
 "A"
 "B"
 "C"
 "A"
 "B"
 "B"
```
