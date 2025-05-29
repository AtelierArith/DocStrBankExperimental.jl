```julia
function studentTest1S(𝐲::UniData;
            refmean::Realo = nothing,
            direction::TestDir = Both(),
            equivalent::Bool = true,
            switch2rand::Int = Int(1e8),
            nperm::Int = 20_000, 
            seed::Int = 1234, 
            verbose::Bool = true) where TestDir <: TestDirection =
```

Univariate [one-sample t-test](https://en.wikipedia.org/wiki/Student's_t-test#One-sample_t-test)  by data permutation. The null hypothesis has form 

$H_0: μ=μ_0$,

where $μ$ is the mean of the observations and $μ_0$ is a reference population mean.

`refmean` is the reference mean ($μ_0$) above. The default is $0$, which is the value used for most tests.

For optional keyword arguments, `direction`, `equivalent`, `switch2rand`, `nperm`, `seed` and `verbose`,  see [here](@ref "Common kwargs for univariate tests").

*Directional tests*

  * For a right-directional test, $μ$ is expected to exceeds $μ_0$. If the opposite is true the test will result in a p-value higehr then 0.5.
  * For a left-directional test, $μ_0$ is expected to exceeds $μ$. If the opposite is true the test will result in a p-value higehr then 0.5.

*Permutation scheme:* the one-sample t-test test is equivalent to a t-test for two repeated measures, the mean of the difference of which  is tested by the one-sample t-test. Under the null hypothesis, the order of the two measurements bears no meaning. The exchangeability scheme consists then in reordering the two measurements in the $N$ observation units.  For a one-sample t-test, this amounts to considering the observations with the observed and switched sign.

*Number of permutations for exact tests:* there are $2^N$ possible ways of reordering the two measurements in the $N$ observations of `y`. For the one-sample t-test, this is the number of possible configurations of the signs of the observations.

**Alias:** `tTest1S` 

Multiple comparisons version: [`studentMcTest1S`](@ref)

Return a [UniTest](@ref) structure.

*Examples*

```julia
using PermutationTests
N=20 # number of observations
y = randn(N) # some random Gaussian data for example
t = tTest1S(y) # test H0: μ(y)=0. By deafult the test is bi-directional

t = tTest1S(y; refmean=1.) # test H0: μ(y)=1
tR = tTest1S(y; direction=Right()) # right-directional test
tL = tTest1S(y; direction=Left()) # Left-directional test
# Force an approximate test with 5000 random permutations
tapprox = tTest1S(y; switch2rand=1, nperm=5000) 
```

**Similar tests**

Typically, the input data is real, but can also be of type integer or boolean. If either `y` is a vector  of booleans or a vector of dicothomous data (only 0 and 1), this function will actually perform a permutation-based  version of the [sign test](https://en.wikipedia.org/wiki/Sign_test). With boolean input, use the [signTest](@ref) function.

Passing as data input the vector of differences of two repeated measurements, this function carries out the  Student's t-test for repeated measurements. If you need such a test you may want to use the [`studentTestRM`](@ref) alias.
