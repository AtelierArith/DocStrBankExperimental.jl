```
levene(observations::Array{Union{Number, Vector{Number}}})
levene(observations::Vector{Number}, factorassignments::Vector{Vector{Any}})
levene(df::DataFrame, observationscolumn::Symbol, factorcolumns::Vector{Symbol})
```

Performs Levene's homogeniety of variance test.

Operates on at least 3 crossed factors (fixed or random) and arbitrarily many random nested factors on balanced data. Levene's test is identical to performing an ANOVA on the absolute deviations of each cell.

If Levene's test is significant, the data is heteroscedastic (variances differ). If it is not, variances could differ or the sample size could be too small to tell.

# Arguments

  * `observations`: Array containing the values to test. For the array, each dimension is a factor level, such that observations[2,5,3] indicates the 2nd level of the first factor, the 5th level of the second factor, and the 3rd level of the third factor. May contain values or vectors of values, where the vector contains replicates. Factors should be ordered with least significant first. For the vector, must provide `factorassignments` to specify factor levels.
  * `factorassignments`: Vector of vectors of integers specifying how each observation is assigned to a factor level. Provide this when `observations` is given as a vector. Factor levels do not have to be consecutive or ordered. Nested factors must reuse factor levels currently.

Notes: Throws an exception if it can tell there are no replicates. Do not use with on any data structure you would pass into `anova()` using `hasrepliates=false`.

Output: `AnovaData` structure containing the test results for each factor.

# Examples

```julia
levene(observations)
```
