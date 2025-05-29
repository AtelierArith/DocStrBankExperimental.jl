cat*collapse(cat*array::CategoricalArray, levels_map::Dict)

Collapses levels in a categorical variable column based on a provided mapping.

# Arguments

`cat_array`: Categorical variable column to collapse. levels_map: A dictionary with the original levels as keys and the new levels as values. Levels not in the keys will be kept the same.

# Returns

Categorical array with the levels collapsed.

# Examples

```jldoctest
julia> cat_array = CategoricalArray(["A", "B", "C", "D", "E"], ordered=true)
5-element CategoricalArrays.CategoricalArray{String,1,UInt32}:
 "A"
 "B"
 "C"
 "D"
 "E"

julia> levels_map = Dict("A" => "A", "B" => "A", "C" => "C", "D" => "C", "E" => "E");

julia> cat_collapse(cat_array, levels_map)
5-element CategoricalArrays.CategoricalArray{String,1,UInt32}:
 "A"
 "A"
 "C"
 "C"
 "E"
```
