```julia
function allPerms(stat::BivStatistic, ns::Int) 

function allPerms(stat::IndSampStatistic, ns::Vector{Int})

function allPerms(stat::RepMeasStatistic, ns::@NamedTuple{n::Int, k::Int})

function allPerms(stat::OneSampStatistic, ns::Int)

```

Total number of systemetic permutations (exact test) for a test statistic given as singleton `stat`  of a given [group](@ref "Statistic groups").

For the `ns` argument see [ns](@ref).

For an exact tests with $N$ observations and $K$ groups/measuremets,  the total number of systematic permutations is

  * for `stat` a `BivStatistic` :$\quad N!$
  * for `stat` a `IndSampStatistic` : $\quad \frac{N!}{N_1! \cdot \ldots \cdot N_K!}$
  * for `stat` a `RepMeasStatistic` : $\quad K!^N$
  * for `stat` a `OneSampStatistic` : $\quad 2^N$

For the number of non-redundant permutations, which is the actual number of permutations that are listed for exact tests, see [`nrPerms`](@ref).

*Examples*

```julia
# Total number of possible permutations for a 1-way ANOVA for indepedent samples 
# test with a total of 18 observations in three balanced groups.
allPerms(AnovaF_IS(), [6, 6, 6]) # -> 17153136

# Total number of possible permutations for a correlation test with 12 observations.
allPerms(PearsonR(), 12) # -> 479001600
```
