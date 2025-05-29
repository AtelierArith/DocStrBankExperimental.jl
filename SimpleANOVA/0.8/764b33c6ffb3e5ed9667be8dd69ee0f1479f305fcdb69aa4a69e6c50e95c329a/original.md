```
anova(observations::Array{Union{Number, Vector{Number}}}, factortypes = FactorType[]; factornames = String[], hasreplicates = true)
anova(observations::Vector{Number}, factorassignments::Vector{Vector{Any}}, factortypes = FactorType[]; factornames = String[], hasreplicates = true)
anova(df::DataFrame, observationscolumn::Symbol, factorcolumns::Vector{Symbol}, factortypes = FactorType[]; factornames = String[])
```

Performs an Analysis of Variance (ANOVA) calculation.

Operates on fixed or random factors, subject/block factors, and nested factors, with or without replicates, on balanced data.

Limitations:

  * If any factors are `random` type, limited to 3-way
  * Repeated measures ANOVA (with subject/block factor) limited to 3 `fixed` factors which may be partitioned as within or among subjects

Operates on up to 3 crossed factors (fixed or random) and arbitrarily many random nested factors, with or without replicates, on balanced data.

# Arguments

  * `observations`: Array containing the values to test. For the array, each dimension is a factor level, such that observations[2,5,3] indicates the 2nd level of the first factor, the 5th level of the second factor, and the 3rd level of the third factor. May contain values or vectors of values, where the vector contains replicates. Factors should be ordered with least significant first. For the vector, must provide `factorassignments` to specify factor levels.
  * `factorassignments`: Vector of vectors of integers specifying how each observation is assigned to a factor level. Provide this when `observations` is given as a vector. Factor levels do not have to be consecutive or ordered. Nested factors must reuse factor levels currently.
  * `factortypes`: Vector indicating the `FactorType` for each factor. Factors must be ordered with `nested` first, then `random`/`measured` or `fixed`/`manipulated` in any order. For repeated measures, `subject` or `block` must appear after within-subject `fixed` and before among-subject `fixed`. If too few values are provided, remaining are assumed to be `fixed`.
  * `factornames`: Vector of names for each factor, excluding the replicate factor. If empty, will be automatically populated alphabetically.
  * `hasreplicates`: Boolean to specify if the first level should be considered

Notes: The last index will be the top factor in the table.

Output: `AnovaData` structure containing the test results for each factor.

# Examples

```julia
anova(observations)                           # N-way fixed-effects ANOVA with replicates (vectors or first dimension)
anova(observations, hasreplicates = false)    # N-way fixed-effects ANOVA without replicates (first dimension)
anova(observations, [random])                 # N-way ANOVA with lower random factor and 1 or 2 upper fixed factors
anova(observations, [random])                 # N-way ANOVA with lower random factor and 1 or 2 upper fixed factors
anova(observations, [fixed, random])          # N-way ANOVA with 1 lower fixed factor, 1 random factor, and 0 or 1 upper fixed factor
anova(observations, [nested, random])         # N-way fixed-effects ANOVA with 1 random nested factor, 1 random factor, and 1-2 fixed factors
anova(observations, [fixed, subject])         # N-way repeated measures ANOVA with 1 within-subjects fixed factor
anova(observations, [fixed, block])           # N-way repeated measures ANOVA with 1 within-block fixed factor
anova(observations, [nested, fixed, subject]) # N-way repeated measures ANOVA with 1 within-subjects fixed factor and 1 nested factor
```

# Glossary

  * observation: The dependent variable.
  * factor: An independent variable.
  * factor level: A value of a factor.
  * balanced: All combinations of factor levels have the same number of observations.
  * crossed factor: A factor with levels that combine with the levels of all other crossed factors.
  * fixed/manipulated factor: A factor with fixed effects (e.g. treatment, concentration, exposure time).
  * random/measured factor: A factor with random effects (e.g. location, individual).
  * nested factor: A random factor where the levels are unique to a combination of crossed factor levels (e.g. replicate).
  * subject/block factor: A nested factor that is subjected to multiple levels of another factor.
  * sum of squares (SS): A measure of variance that is dependent on sample size. Also called "sum of squared deviations."
  * degrees of freedom (DF, ν): The number of bins in which the values could have been moved, if random.
  * mean square (MS): SS / DF. Corrects for the larger variance expected if random values can be assigned to more bins. Also called "mean squared error" or "mean squared deviation."
  * F-statistic: The division of MS values produce a result belonging to the "F distribution", the shape of which depends on the DF of the numerator and error. The location of this value on the distribution provides the p-value.
  * p-value: The probability that, if all measurements had been drawn from the same population, you would obtain data at least as extreme as contained in your observations.
  * effect size (ω²): The standardized difference in the measurement caused by the factor. This is the generalized version which is largely stable with respect to study design.
