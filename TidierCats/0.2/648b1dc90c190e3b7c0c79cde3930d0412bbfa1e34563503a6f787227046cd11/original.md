```
cat_lump_min(cat_array, min::Int, other_level::String = "Other")
```

Lumps infrequent levels in a categorical array into an 'other' level based on minimum count.

# Arguments

  * `cat_array`: Categorical array to lump
  * `min`: Minimum count threshold. Levels with counts below this will be lumped.
  * `other_level`: The level name to lump infrequent levels into. Default is "Other".

# Returns

Categorical array with levels lumped.

# Examples

```jldoctest  julia> cat_array = CategoricalArray(["A", "B", "B", "C", "C", "D"]) 6-element CategoricalArrays.CategoricalArray{String,1,UInt32}:  "A"   "B"  "B"  "C"   "C"  "D"

julia> cat*lump*min(cat_array, 2)   6-element CategoricalArrays.CategoricalArray{String,1,UInt32}:  "A"  "B"  "B"  "Other"  "Other"  "Other"  ```
