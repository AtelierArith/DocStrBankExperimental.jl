```
cat_infreq(cat_array)
```

Orders the levels in a categorical array by their frequency, with the most common level first.

# Arguments

`cat_array`: Input categorical array.

# Returns

Categorical array with levels reordered by frequency.

# Examples

```jldoctest
julia> cat_array = CategoricalArray(["A", "B", "B"], ordered=true)
3-element CategoricalArrays.CategoricalArray{String,1,UInt32}:
 "A"
 "B"
 "B"

julia> cat_infreq(cat_array)
3-element CategoricalArrays.CategoricalArray{String,1,UInt32}:
 "A"
 "B"
 "B"
```
