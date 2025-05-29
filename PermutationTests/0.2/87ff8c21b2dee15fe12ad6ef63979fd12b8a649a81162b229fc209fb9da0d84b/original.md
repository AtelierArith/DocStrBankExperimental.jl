```julia
function correlationTest(x::UniData, y::UniData;
            direction::TestDir = Both(),
            equivalent::Bool = true,
            switch2rand::Int = Int(1e8), 
            nperm::Int = 20_000, 
            seed::Int = 1234, 
            standardized::Bool = false, 
            centerd::Bool = false,
            verbose::Bool = true) where TestDir <: TestDirection
```

Univariate [Pearson product-moment correlation test](https://en.wikipedia.org/wiki/Pearson_correlation_coefficient#Testing_using_Student's_t-distribution)  by data permutation. The null hypothesis has form 

$H_0: r_{(x,y)}=0$,

where $r_{(x,y)}$ is the correlation between the two input data vectors, `x` and `y`, typically real, both holding $N$ observations.

For optional keyword arguments, `direction`, `equivalent`, `switch2rand`, `nperm`, `seed` and `verbose`,  see [here](@ref "Common kwargs for univariate tests").

If `standardized` is true, both `x` and `y` are assumed standardized (zero mean and unit standard deviation). Provided that the input data is standardized, the test provides the same p-value, however it can be executed faster as in this case the cross-product is equivalent to the Pearon *r* statistic (see [Statistic](@ref)).

If `centered` is true, both `x` and `y` are assumed centered (zero mean). The test provides the same p-value, however it can be executed faster if the test is bi-directional  as in this case the equivalent statistic, the covariance, reduces to the cross-product divided by N.

If neither `standardized` nor `centered` is true, the data will be standardized to execute a faster test using the cross-product as test-statistic.

*Directional tests*

  * For a right-directional test, the correlation is expected to be positive. A negative correlation will result in a p-value higehr then 0.5.
  * For a left-directional test, the correlation is expected to be negative. A positive correlation will result in a p-value higehr then 0.5.

*Permutation scheme:* under the null hypothesis, the position of the observations in the data input vectors bears no meaning. The exchangeability scheme consists then in shuffling the observations of vector `x` or vector `y`. *PermutationTests.jl* shuffles the observations in `x`. 

*Number of permutations for exact tests:* there are $N!$ possible ways of reordering the $N$ observations in `x`.

*Aliases:* `rTest!`, [`trendTest!`](@ref)

*Multiple comparisons version:* [correlationMcTest!](@ref)

Return a [UniTest](@ref) structure.

*Examples*

```julia
using PermutationTests
N=10 # number of observations
x, y = randn(N), randn(N) # some random Gaussian data for example
t = rTest(x, y) # by deafult the test is bi-directional
```

```@julia
tR = rTest(x, y; direction=Right()) # right-directional test
tL = rTest(x, y; direction=Left()) # Left-directional test
# Force an approximate test with 5000 random permutations
tapprox = rTest(x, y; switch2rand=1, nperm=5000) 
```

**Similar tests**

Typically, the input data is real, but can also be of type integer or boolean. If either `x` or `y` is a vector  of booleans or a vector of dicothomous data (only 0 and 1), this function will actually perform a permutation-based  version of the [point bi-serial correlation test](https://en.wikipedia.org/wiki/Point-biserial_correlation_coefficient). However, as shown in the preceeding link, the point bi-serial correlation test is equivalent to  the t-test for independent sample, thus it can be tested using the t-test for independent samples, which will need many less permutations as compared to a correlation test for an exact test  (see examples below). A dedicated function in available with name [`pointBiSerialTest`](@ref), which is an alias for [`studentTestIS`](@ref) and allowa the choice to run the test using a  correlation- or t-test statistic.

If `x` or `y` represent a *trend*, for example a linear trend given by `[1, 2,...N]`,  we otain the permutation-based trend correlation test, which can be used to test the fit of any type of regression of `y` on `x` - see [trendTest](@ref).    

if `y` is a shifted version of `x` with a lag $l$, this function will test the significance of the  *autocorrelation at lag $l$, see the page [Create your own test](@ref).

*Examples*

```julia
# Point bi-serial correlation test
using PermutationTests
N=10 # number of observations
x=[0, 0, 0, 0, 1, 1, 1, 1, 1, 1]
y = rand(N)
t = rTest(x, y) 

# Exactly the same test can be obtained as a t-test for independent sample,
# but much faster as for an exact test the latter needs only 210 permutations 
# while the former needs 3628800 permutations.
# This is available with a dedicated function
t2=pointBiSerialTest(y, [4, 6])
println(t.p ≈ t2.p ? "OK" : "error")
```
