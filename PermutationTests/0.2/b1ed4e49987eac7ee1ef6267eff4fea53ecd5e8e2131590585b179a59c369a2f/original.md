```julia
function signMcTest(Y::Union{AbstractVector{BitVector}, AbstractVector{Vector{Bool}}};
            direction::TestDir = Both(),
            switch2rand::Int= max(Int(1e8) ÷ length(𝐘), Int(1e4)),
            nperm::Int = 20_000, 
            seed::Int = 1234, 
            verbose::Bool = true,
            #
            stepdown::Bool = true,
            fwe::Float64 = 0.05,
            threaded::Bool = Threads.nthreads()>=4) where TestDir <: TestDirection

```

Multiple comparisons [sign test](https://en.wikipedia.org/wiki/Sign_test) by data permutation. 

Run $M$ sign tests simultaneously.The null hypotheses have form 

$H_0(m): E_m(true)=E_m(false), \quad m=1...M$,

where $E_m(true)$ and $E_m(false)$ are the expected number of true and false occurrences, respectively, in the $m^{th}$ hypothesis.

`Y` ia a vector of $M$ vectors holding each $N$ booleans.

For optional keyword arguments, `direction`, `switch2rand`, `nperm`, `seed`, `verbose`, `stepdown`, `fwe` and `threaded` see [here](@ref "Common kwargs for multiple comparisons tests"). 

*Directional tests, permutation scheme and number of permutations for exact tests:* as per  *univariate version* [`signTest`](@ref)

Return a [MultcompTest](@ref) structure.

*Examples*

```julia
using PermutationTests
N=20; # number of observations
M=100; # number of hypotheses
Y = [rand(Bool, N) for m=1:M]; # some random Gaussian data for example
t = signMcTest(Y) # By deafult the test is bi-directional

tR = signMcTest(Y; direction=Right()) # right-directional test
tL = signMcTest(Y; direction=Left()) # Left-directional test

# Force an approximate test with 5000 random permutations
tapprox = signMcTest(Y; switch2rand=1, nperm=5000) 
```
