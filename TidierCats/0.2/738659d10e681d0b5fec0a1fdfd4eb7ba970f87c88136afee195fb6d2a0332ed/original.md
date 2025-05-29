```
cat_lump(cat_array, n::Int)
```

Orders the levels in a categorical array by their frequency and keeps only the 'n' most common levels. All other levels are replaced by "Other".

Arguments `cat_array`: Input categorical array. `n`: Number of levels to keep as they are, the rest become "Other"

# Returns

Categorical array with the least frequent levels lumped as "Other". 

# Examples

```jldoctest
julia> cat_array = CategoricalArray(["A", "B", "C", "A", "B", "B", "D", "E", "F"], ordered=true)
9-element CategoricalArrays.CategoricalArray{String,1,UInt32}:
 "A"
 "B"
 "C"
 "A"
 "B"
 "B"
 "D"
 "E"
 "F"
```
