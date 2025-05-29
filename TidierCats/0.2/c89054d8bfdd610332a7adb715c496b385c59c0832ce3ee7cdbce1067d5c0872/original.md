```
cat_lump_prop(cat_array, prop::Float64, other_level::String = "Other")
```

Lumps infrequent levels in a categorical array into an 'other' level based on proportion threshold.

# Arguments

  * `cat_array`: Categorical array to lump
  * `prop`: Proportion threshold. Levels with proportions below this will be lumped.
  * `other_level`: The level name to lump infrequent levels into. Default is "Other".

# Returns

Categorical array with levels lumped based on proportion.

# Examples

```jldoctest julia> cat_array = CategoricalArray(["A", "B", "B", "C", "C", "D"]) 6-element CategoricalArrays.CategoricalArray{String,1,UInt32}:  "A"  "B"   "B"  "C"  "C"   "D"

julia> cat*lump*prop(cat_array, 0.3) 6-element CategoricalArrays.CategoricalArray{String,1,UInt32}:  "A"  "B"  "B"  "Other"   "Other"  "Other"  ```
