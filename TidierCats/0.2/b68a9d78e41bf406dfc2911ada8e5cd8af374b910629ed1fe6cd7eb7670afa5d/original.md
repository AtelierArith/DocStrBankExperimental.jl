```
cat_replace_missing(cat_array::CategoricalArray, missing_level::String = "missing")
```

Replaces missing values within a CategoricalArray with a placeholder string.

# Arguments

  * `cat_array`: Categorical array to lump
  * `missing_level`: The string that will be used inplace of missing values.

# Returns

Categorical array without any missing elements. 

# Examples

```jldoctest
julia> cat_array = CategoricalArray(["apple", "tomato", missing, "dear"])
4-element CategoricalArrays.CategoricalArray{Union{Missing, String},1,UInt32}:
 "apple"
 "tomato"
 missing
 "dear"

julia> cat_replace_missing(cat_array)
4-element CategoricalArrays.CategoricalArray{String,1,UInt32}:
 "apple"
 "tomato"
 "missing"
 "dear"

julia> cat_replace_missing(cat_array, "unknown")
4-element CategoricalArrays.CategoricalArray{String,1,UInt32}:
 "apple"
 "tomato"
 "unknown"
 "dear"
```
