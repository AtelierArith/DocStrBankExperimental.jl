```julia
function _permMcTest!(x, Y, ns::nsType, stat::Stat, asStat::AsStat;
            standardized::Bool=false, centered::Bool=false, 
            stepdown::Bool = true,
            fwe::Float64 = 0.05,
            nperm::Int = 20000, 
            fstat::Function = abs,
            compfunc::Function = >=,
            switch2rand::Int = Int(1e8),
            seed::Int = 1234,
            threaded::Bool = Threads.nthreads()>=4,
            verbose::Bool = true,
            cpcd = nothing) where {Stat<:Statistic, AsStat<:Statistic}
```

This function ultimately performs all **multiple comparisons permutation tests** implemented in *PermutationsTests.jl*,  both *exact* and *approximate* (Monte Carlo). 

For running tests use the [multiple comparisons test functions](@ref "Multiple comparisons tests"). You need this function only for [creating your own tests](@ref "Create your own test").

The step-down version of the test is performed if `stepdown` is true (default). In this case the `fwe` (family-wise error) rate is used for rejection at each step (default=0.05).

Rewrite `x` and/or `Y`, depending on the test performed.

For the `ns` argument see [ns](@ref).

`stat` can be a singleton of the [Statistic](@ref) type or a user-defined singleton of this type  to be used as argument of two functions implemented by the user to compute the observed and permuted test statistics, see [create your own test](@ref "Create your own test").

!!! warning
    In contrast to univariate tests, equivalent statistics are not possible for multiple comparison tests,  with the exception of `CrossProd()` if the data has been standardized and `Covariance()` if the data  has been centered and those only for correlation-like tests.

    The test statistics that must be used as `Stat` for the other kinds of test if a singleton of the  [Statistic](@ref) type is used are `AnovaF_IS()`, `StudentT_IS()`, `AnovaF_RM()`, and `StudentT_1S()`.


`asStat` is a singleton of the [Statistic](@ref) type. It is used to determine the permutation scheme  and for this purpose it will be passed to [`genPerms`](@ref) and [`nrPerms`](@ref).

`asStat` determines also the input data format if you declare your own `stat` type. In this case the two functions you write for computing the observed and permuted statistics will take the `x` and  `Y` arguments as it follows. 

For `Stat` belonging to [group](@ref "Statistic groups")

  * `BivStatistic` : `x` is a fixed vector with $N$ elements and `Y` an an $M$-vector of $N$-vectors. The $M$ bivariate statistics between `x` and the $y_m$ vectors of `Y` are tested simultaneously. `ns` is ignored.
  * `IndSampStatistic` : we have $K$ groups and $N=N_1+...+N_K$ total observations; `Y` is an $M$-vector, each one holding all observations for the $m^{th}$ hypothesis in a single vector. The $m^{th}$ vector $y_m$ concatenates the observations for all groups such as [y[m][1];...;y[m][K]]. `x` is the [`membership(::IndSampStatistic)`](@ref) vector, common to all hypotheses. For example, for $K=2$, $N_1=2$ and $N_2=3$, `x=[1, 1, 2, 2, 2]`.
  * `RepMeasStatistic` : we have $K$ measures (*e.g.*, treatements) and $N$ subjects; `Y` is an M-vector, each one holding the $K*N$ observations for the $m^{th}$ hypothesis in a single vector. The $m^{th}$ vector $y_m$ is such as `[Y[m][1];...;Y[m][N]]`, where each vector Y[1][n], for $n=1…N$, holds the observations for the $K$ treatments and `x=collect(1:K*N)` (see [`membership(::RepMeasStatistic)`](@ref)).
  * `OneSampStatistic` : We have $N$ observations (*e.g.*, subjects); `Y` is an $M$-vector, each one holding the $N$ observations and `x=ones(Int, N)` (see [`membership(::OneSampStatistic)`](@ref)).

!!! note "Nota Bene"
    In all cases `x` is treated as the permutation vector that will be permuted before calling the [`testStatistic`](@ref) function for each of the elements in `Y`.


Optional keyword arguments `switch2rand`, `nperm`, `standardized`, `centered`, `seed`, `fstat`, `compfunc` and `verbose` have the same meaning as in the [`_permTest!`](@ref) function.

If `threaded` is true (default) the function is multi-threaded if the product of the number of hypotheses,      observations, and permutations exceed 500 millions. If you have unexpected problems with the function, try setting `threaded` to false.

For the `cpcd` and `kargs...` arguments, see [create you own test](@ref "Create your own test").

Return a [MultcompTest](@ref) structure.

The number of executed steps $S$ can be retrived as the length of the `.rejections` field  of the returned structure. 

*Examples*

```julia
using PermutationTests
N, M = 8, 100 # 100 hypotheses, N=8
x=randn(N)
Y=[randn(N) for m=1:M]
# bi-directional exact test of the correlation between x and 
# all the M vector in Y.
T12 = _permMcTest!(x, Y, N, PearsonR(), PearsonR())
T12.p
T12.stat
#...

# bi-directional exact test. Faster test by data standardization 
T12_2 = _permMcTest!(μ0σ1(x), [μ0σ1(y) for y in Y], N, CrossProd(), PearsonR(); 
                    standardized=true) 

# left-directional exact test.
T12_3 = _permMcTest!(μ0σ1(x), [μ0σ1(y) for y in Y], N, CrossProd(), PearsonR(); 
                    standardized=true, fstat=flip)

# as above, but force an approximate test
T12_4 = _permMcTest!(μ0σ1(x), [μ0σ1(y) for y in Y], N, CrossProd(), PearsonR(); 
                    standardized=true, fstat=flip, switch2rand=1)

# the same using 5000 random permutations
T12_4 = _permMcTest!(μ0σ1(x), [μ0σ1(y) for y in Y], N, CrossProd(), PearsonR(); 
                    standardized=true, fstat=flip, switch2rand=1, nperm=5000)
```

To check more examples, see the *multcompTests_API.jl* unit located in the *src* github folder and function `test_multicompTests()` in the *runtests.jl* unit located in the *test* github folder.
