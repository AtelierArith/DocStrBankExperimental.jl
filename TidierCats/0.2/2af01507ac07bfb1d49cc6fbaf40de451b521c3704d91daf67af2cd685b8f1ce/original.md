```
cat_recode(cat_array::Union{CategoricalArray, AbstractVector}; kwargs...)
```

Recodes the levels in a categorical array based on a provided mapping.

# Arguments

  * `cat_array`: Categorical array to recode
  * `kwargs`: A dictionary with the original levels as keys and the new levels as values. Levels not in the keys will be kept the same.

# Returns

Categorical array with the levels recoded.

# Examples

```jldoctest
julia> x = CategoricalArray(["apple", "tomato", "banana", "dear"]);

julia> println(levels(cat_recode(x, fruit = ["apple", "banana"], nothing = ["tomato"])))
["fruit", "nothing", "dear"]
```
