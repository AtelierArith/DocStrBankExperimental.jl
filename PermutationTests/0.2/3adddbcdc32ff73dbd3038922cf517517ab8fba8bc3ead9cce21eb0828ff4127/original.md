```julia
signTest(𝐲::Union{BitVector, Vector{Bool}};
            direction::TestDir = Both(),
            equivalent::Bool = true,
            switch2rand::Int = Int(1e8),
            nperm::Int = 20_000, 
            seed::Int = 1234, 
            verbose::Bool = true) where TestDir <: TestDirection =

```

Univariate [sign test](https://en.wikipedia.org/wiki/Sign_test) by data permutation. The null hypothesis has form 

$H_0: E(true)=E(false)$,

where $E(true)$ and $E(false)$ are the expected number of true and false occurrences, respectively.

`y` ia a vector of $N$ booleans.

For optional keyword arguments, `direction`, `equivalent`, `switch2rand`, `nperm`, `seed` and `verbose`,  see [here](@ref "Common kwargs for univariate tests").

*Directional tests*

  * For a right-directional test, $E(true)$ is expected to exceeds $E(false)$. If the opposite is true the test will result in a p-value higehr then 0.5.
  * For a left-directional test, $E(false)$ is expected to exceeds $E(true)$. If the opposite is true the test will result in a p-value higehr then 0.5.

Permutation scheme and number of permutations for exact tests: as per [`studentTest1S`](@ref). 

The significance of the univariate sign test can be obtained much more efficiently using the binomial distribution. This permutation test is therefore not useful at all in the univariate case,  however, its multiple comparison version allows the control of the family-wise error rate by data permutations.

**Multiple comparisons version**

[`signMcTest`](@ref)

Return a [UniTest](@ref) structure.

*Examples*

```julia
using PermutationTests
N=20; # number of observations
y = rand(Bool, N); # some random Gaussian data for example
t = signTest(y) # By deafult the test is bi-directional

tR = signTest(y; direction=Right()) # right-directional test
tL = signTest(y; direction=Left()) # Left-directional test
# Force an approximate test with 5000 random permutations
tapprox = signTest(y; switch2rand=1, nperm=5000) 
```
