```julia
function _permTest!(x, y, ns::nsType, stat::Stat, asStat::AsStat;
                    standardized::Bool=false, centered::Bool=false, 
                    nperm::Int = 20000, 
                    fstat::Function = abs,
                    compfunc::Function = >=,
                    switch2rand::Int = Int(1e8),
                    seed::Int = 1234,
                    verbose::Bool = true,
                    cpcd = nothing,
                    kwargs...) where {Stat<:Statistic, AsStat<:Statistic}
```

This function ultimately performs all **univariate permutation tests** implemented in *PermutationsTests.jl*,  both *exact* and *approximate* (Monte Carlo). 

For running tests use the [univariate test functions](@ref "Univariate tests"). You need this function only for [creating your own tests](@ref "Create your own test").

Rewrite `x` and/or `y`, depending on the test performed.

For the `ns` argument see [ns](@ref).

`stat` can be a singleton of the [Statistic](@ref) type or a user-defined singleton of this type  to be used as argument of a function implemented by the user to compute both the observed and permuted test statistics, see [create your own test](@ref "Create your own test").

`asStat` is a singleton of the [Statistic](@ref) type. It is used to determine the permutation scheme  and for this purpose it will be internally passed to [`genPerms`](@ref) and [`nrPerms`](@ref).

`asStat` determines also the input data format if you declare your own `stat` type. In this case the function you write for computing the observed and permuted test statistic will take the `x` and  `y` arguments as it follows: 

For `Stat` belonging to [group](@ref "Statistic groups")

  * `BivStatistic` : `x`, `y` are the two vectors of $N$ elements each for which the bivariate statistic is to be tested. `ns` is ignored.
  * `IndSampStatistic` : we have $K$ groups and $N=N_1+...+N_K$ total observations; `y` holds all observations in a single vector such as `[y1;...;yK]` and `x` is the [`membership(::IndSampStatistic)`](@ref) vector. For example, for $K=2$, $N_1=2$ and $N_2=3$, `x=[1, 1, 2, 2, 2]`.
  * `RepMeasStatistic` : we have $K$ measures (*e.g.*, treatements) and $N$ subjects; `y` holds the  $K*N$ observations in a single vector such as `[y1;...;yN]`, where each vector $y_i$, for $i=1...N$, holds the observation at the $K$ treatments and `x=collect(1:K*N)` (see [`membership(::RepMeasStatistic)`](@ref)).
  * `OneSampStatistic` : We have $N$ observations (*e.g.*, subjects); `y` holds the $N$ observations and `x=ones(Int, N)` (see [`membership(::OneSampStatistic)`](@ref)).

!!! note "Nota Bene"
    In all cases `x` is treated as the permutation vector that will be permuted before calling the [`testStatistic`](@ref) function.


For `length(x)>30` the approximate test is performed in all cases, 

otherwise,

if the number of systematic permutations exceeds `switch2rand` the approximate test is performed  using `nperm` random permutations (default 20000), 

otherwise, 

the exact test is performed. 

`switch2rand` defaults to 1e8.  To perform approximate tests in all cases, set `switch2rand`, for example, to 1. 

If `stat` is a `BivStatistic`, it optionally uses kwargs `standardized` or `centered` to compute them faster, see for example [`correlationTest`](@ref).

`seed` is the initial seed for generating random permutations (not used for exact tests).  To use a random seed, pass `seed=0`. For `seed` any natural number, the test will be reproducible.

`fstat` is a function applied to the test statistic. By default this is the julia `abs` function,  which takes the absolute value, hence yieds a bi-directional test for a test statistic distributed symmetrically around zero. For a right-directional test using such test statistics pass here `identity`.  For a left-directional using such test statistics pass here [`flip`](@ref).

`compfunc` is the function to compare the observed statistics to the permuted statistics.  The default function is `>=`. Don't change it unless you have studied the code of the function.

If `verbose` is true, print some information in the REPL while running the test.  Set to false if you run benchmarks. The default is true.

For the `cpcd` and `kwargs...` argument, see [create you own test](@ref "Create your own test").

Return a [UniTest](@ref) structure.

*Examples*

```julia
using PermutationTests
x=randn(6)
y=randn(6) 
# bi-directional exact test of the correlation between x and y
t8 = _permTest!(μ0(x), μ0(y), length(x), Covariance(), Covariance(); centered=true) 
t8.p
t8.stat
#...

# make a left-directional test and standardize the data
t8_2 = _permTest!(μ0σ1(x), μ0σ1(y), length(x), Covariance(), Covariance(); 
        standardized=true, fstat=flip) 

# the same but force an approximate test
t8_3 = _permTest!(μ0σ1(x), μ0σ1(y), length(x), Covariance(), Covariance(); 
        standardized=true, fstat=flip, switch2rand=1) 

# the same using 5000 random permutations
t8_4 = _permTest!(μ0σ1(x), μ0σ1(y), length(x), Covariance(), Covariance(); 
        standardized=true, fstat=flip, switch2rand=1, nperm=5000) 
```

To check more examples, see the *uniTests_API.jl* unit located in the *src* github folder and function `test_unitests()` in the *runtests.jl* unit located in the *test* github folder.
