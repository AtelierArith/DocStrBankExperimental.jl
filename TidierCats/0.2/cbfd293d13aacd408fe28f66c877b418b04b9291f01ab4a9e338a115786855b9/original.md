```
cat_other(cat_array::CategoricalArray, other_level::String="Other")
```

Replaces all levels in a categorical array with the 'other' level.

# Arguments

  * `cat_array`: Categorical array to replace levels
  * `other_level`: The level name to replace all levels with. Default is "Other".

# Returns

Categorical array with all levels replaced by the 'other' level.

# Examples

```jldoctest
julia> cat_array = CategoricalArray(["A", "B", "C", "D", "E"]);

julia> cat_other(cat_array, drop = ["A", "B"])
5-element CategoricalArrays.CategoricalArray{String,1,UInt32}:
 "Other"
 "Other"
 "C"
 "D"
 "E"
```
