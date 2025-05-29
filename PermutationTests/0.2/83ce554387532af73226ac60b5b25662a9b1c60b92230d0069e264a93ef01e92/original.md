```julia
function nrPerms(stat::Union{BivStatistic, OneSampStatistic}, ns::Int, total, 
                direction::TestDir, design::Assign=Balanced()) 

function nrPerms(stat::IndSampStatistic, ns::Vector{Int}, total, 
                direction::TestDir, design::Assign)

function nrPerms(stat::RepMeasStatistic, ns::@NamedTuple{n::Int, k::Int}, total, 
                direction::TestDir, design::Assign=Balanced())
                
    where {TestDir<: TestDirection, Assign <: Assignment}

```

Number of non-redundant systemetic permutations. This is the actual number of permutations  that are listed for an exact test.

Depending on the test direction and design, there may exists redundant permutations, *i.e.*,  permutations that yields the same test statistic.  These permutations are therefore eliminated, yielding a faster test.

`stat` is the test statistic used by the test given as a singleton.  It belongs to one [group](@ref "Statistic groups")  of test statistics.

For the `ns` argument see [ns](@ref).

`total` is the total number of systematic permutations. In order to avoid errors, it should be given  as the resut of the [`allPerms`](@ref) function.

`direction` is a singleton of type [TestDirection](@ref).

`design` is a singleton of type [Assignment](@ref). In order to avoid errors,  use the result of [`assignment`](@ref) as argument `design`. 

With `stat` a `IndSampStatistic` and a balanced design, the non-redundant permutations are $\frac{total}{K!}$,  with $K$ the number of groups.

With `stat` a `RepMeasStatistic` and a bi-directional tests, the non-redundant permutations are $\frac{total}{K!}$, with $K$ the number of measures.

For `stat` a `BivStatistic` or a `OneSampStatistic` return `total`, that is, there is no possible redundancy.

Note that the elimination of redundant permutations is rarely implemented in software packages for permutation tests.

*Examples*

```julia
using PermutationTests
# Number of possible permutations for a 1-way ANOVA for indepedent samples 
# test with a total of 18 observations in three balanced groups.
ns=[6, 6, 6]
total=allPerms(AnovaF_IS(), ns) # -> 17153136
# Number of non-redundant permutations that will be actually listed
# to perform the test.
design=assignment(AnovaF_IS(), ns)
nrPerms(AnovaF_IS(), ns, total, Both(), design) # -> 2858856
```
