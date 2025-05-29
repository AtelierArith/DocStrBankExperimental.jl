```julia
function correlationMcTest(x::UniData, Y::UniDataVec;
            direction::TestDir = Both(),
            switch2rand::Int = max(Int(1e8) ÷ length(𝐘), Int(1e4)), 
            nperm::Int = 20_000, 
            seed::Int = 1234, 
            verbose::Bool = true, 
            #
            standardized::Bool = false,
            #
            stepdown::Bool = true,
            fwe::Float64 = 0.05,
            threaded::Bool = Threads.nthreads()>=4) where TestDir <: TestDirection
```

Multiple comparisons [Pearson product-moment correlation test](https://en.wikipedia.org/wiki/Pearson_correlation_coefficient#Testing_using_Student's_t-distribution)  by data permutation. 

Run $M$ correlation tests simultaneously.  The input data are a fixed vector `x` and $M$ vectors given as `Y`, a vector of $M$ vectors $y_1,...,y_M$. 

`x` and all vectors in `Y` must have equal length. 

The $M$ null hypotheses have form 

$H_0(m):r_{(x, y_m)}=0, \quad m=1...M$, 

where $r_{x,y_m}$ is the Pearson correlation coefficient between vector `x` and the $m^{th}$ vector of `Y`.

For optional keyword arguments, `direction`, `switch2rand`, `nperm`, `seed`, `verbose`, `stepdown`, `fwe` and `threaded`, see [here](@ref "Common kwargs for multiple comparisons tests").

If `standardized` is true, both `x` and all vectors of `Y` are assumed standardized (zero mean and unit standard deviation). With standardized input data the test can be executed faster as in this case the cross-product is actually the correlation.  If `standardized` is false, the data will be standardized to execute a faster test.

*Directional tests, permutation scheme and number of permutations for exact tests:* as per  *univariate version* [`correlationTest`](@ref)

*Aliases:* `rMcTest`, [`trendMcTest`](@ref) 

Return a [MultcompTest](@ref) structure.

*Examples*

```julia
using PermutationTests
N=10; # number of observations
M=100; # number of tests
x=randn(N);
Y=[randn(N) for i=1:M];
t=rMcTest(x, Y) # bi-directional test
```

```julia
tR=rMcTest(x, Y; direction=Right()) # right-directional test
tL=McTest(x, Y; direction=Left()) # left-directional test
tMC=rMcTest(x, Y; switch2rand=1) # Force a monte carlo test
# Force a monte carlo test and performs 50K permutations
t5K=rMcTest(x, Y; switch2rand=1, nperm= 50_000) 
tnoSD=rMcTest(x, Y; stepdown=false) # don't do stepdown
tnoMT=rMcTest(x, Y; threaded=false) # don't run it multithreaded
t001=rMcTest(x, Y; fwe=0.01) # stepdown rejects at 0.01 level instead of 0.05
```

**Similar tests**

See [correlationTest](@ref)
