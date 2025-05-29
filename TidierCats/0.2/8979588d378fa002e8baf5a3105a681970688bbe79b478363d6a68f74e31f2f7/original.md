```
cat_reorder(cat_var::AbstractVector, order_var::AbstractVector, fun::String, desc::Bool=true)
```

Reorders the levels in a categorical variable column based on a summary statistic calculated from another variable.

Arguments `cat_var`: Categorical variable column to reorder. `order_var`: Variable to calculate the summary statistic from. `fun`: Function to calculate the summary statistic. Options are "mean" and "median". `desc`: If true, the levels are ordered in descending order of the summary statistic.

# Returns

Categorical array with the levels reordered.

# Examples

```jldoctest
julia> cat_var = String["A", "B", "A", "B", "A", "B", "C", "C", "C"];
       order_var = [1, 2, 3, 4, 5, 6, 7, 8, 9];
       cat_reorder(cat_var, order_var, "mean")
9-element CategoricalArrays.CategoricalArray{String,1,UInt32}:
 "A"
 "B"
 "A"
 "B"
 "A"
 "B"
 "C"
 "C"
 "C"
```
