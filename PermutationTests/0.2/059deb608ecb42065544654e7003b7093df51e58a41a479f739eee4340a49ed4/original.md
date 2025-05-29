```julia
function studentMcTest1S(Y::UniDataVec;
            refmean::Realo = nothing,
            direction::TestDir = Both(),
            switch2rand::Int = max(Int(1e8) ÷ length(𝐘), Int(1e4)),
            nperm::Int = 20_000, 
            seed::Int = 1234, 
            verbose::Bool = true,
            #
            stepdown::Bool = true,
            fwe::Float64 = 0.05,
            threaded::Bool = Threads.nthreads()>=4) where TestDir <: TestDirection 
```

Multiple comparison [one-sample t-test](https://en.wikipedia.org/wiki/Student's_t-test#One-sample_t-test)  by data permutation. 

Run $M$ one-sample t-tests simultaneously. The null hypotheses have form 

$H_0(m): μ_m=μ_0, \quad m=1...M$,

where $μ_m$ is the mean of the observations for the $m^{th}$ hypothesis and $μ_{0}$ is a reference  population mean.

`refmean` is the reference mean ($μ_0$) above. The default is `0.0`, which is the value needed in most situations.

`Y` is a vector of $M$ vectors holding each the $N$ observations which mean is to be compared to $μ_0$.

For optional keyword arguments, `direction`, `switch2rand`, `nperm`, `seed`, `verbose`, `stepdown`, `fwe` and `threaded` see [here](@ref "Common kwargs for multiple comparisons tests"). 

*Directional tests, permutation scheme and number of permutations for exact tests:* as per *univariate version* [`studentTest1S`](@ref)

*Alias:* `tTest1S` 

Return a [MultcompTest](@ref) structure.

*Examples*

```julia
using PermutationTests
N=20 # number of observations
M=100 # number of hypotheses
y = [randn(N) for m=1:M]; # some random Gaussian data for example
t = tMcTest1S(Y) # By deafult the test is bi-directional

tR = tMcTest1S(Y; direction=Right()) # right-directional test
tL = tMcTest1S(Y; direction=Left()) # Left-directional test

# Force an approximate test with 5000 random permutations
tapprox = tMcTest1S(Y; switch2rand=1, nperm=5000) 

# test H0m: μ(ym)=1.5: all will be rejected as the expected mean is 0.0
t1 = tMcTest1S(Y; refmean=1.5) 
```

**Similar tests**

See [`studentTest1S`](@ref)
