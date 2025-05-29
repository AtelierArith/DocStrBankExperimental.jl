```
find_missing_sums(missed,de::MeanfieldEquations)
```

From a initial set of differential equation of averages, find all averages that are missing and inside a Symbolic sum. If a missing average contains one of the summation indices used in the equations, the [`Index`](@ref) will be exchanged according to the keyword argument `extra_indices`. Uses [`find_missing`](@ref).

# Arguments

*`missed`: A initial Vector of averages, representing the missed averages before calling     this method. *`de`: The set of equations, in which the missing averages are searched in.

# Optional arguments

*`extra_indices`: A Vector of symbols, representing extra [`Index`](@ref) entities, which are     needed and created in the process of finding missing terms. This argument is required, if the order     of the Meanfield-Equations exceeds 1 and the number of given symbols must match the corresponding order. *`checking`: A Bool defining if the algorithm checks for adjoint values and duplicates, before adding a found     average into the `missed` vector. *`scaling`: A Bool defining the way how averages are added to the `missed` vector. If true only averages, whose     operators (without indices) are not already inside the `missed` vector will be added.

see also: [`find_missing`](@ref), [`indexed_meanfield`](@ref), [`meanfield`](@ref), [`find_missing_sums`](@ref)
