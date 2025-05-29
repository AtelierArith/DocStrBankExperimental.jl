```julia
function table2vec(table::Matrix{I}, stat::IndSampStatistic) 

function table2vec(tables::AbstractVector{Matrix{I}}, stat::IndSampStatistic) 

function table2vec(table::Matrix{I}, stat::RepMeasStatistic) 

function table2vec(tables::AbstractVector{Matrix{I}}, stat::RepMeasStatistic) 

    where I<:Int

```

Format tables of dicothomous data so as to create data input for test functions. 

Return the 2-tuple holding the formatted table as a vector (for univariate test) or a vector of vectors (for multiple comparisons tests) and the appropriate argument [ns](@ref).

You do not need to use these functions in general, as they are called internally by the test functions. However they may be useful if you [create your own test](@ref "Create your own test") for dicothomous data.

`stat` is a singleton of the [Statistic](@ref) type, that is, a test-statistic belonging to one of the [group of test statistics](@ref "Statistic groups").

For the usage of these functions, see the documentation of the test functions using them:

**Univariate test functions**

  * [`chiSquaredTest`](@ref)
  * [`fisherExactTest`](@ref)
  * [`cochranqTest`](@ref)
  * [`mcNemarTest`](@ref)

**Multiple comparisons test functions**

  * [`chiSquaredMcTest`](@ref)
  * [`fisherExactMcTest`](@ref)
  * [`cochranqMcTest`](@ref)
  * [`mcNemarMcTest`](@ref)
