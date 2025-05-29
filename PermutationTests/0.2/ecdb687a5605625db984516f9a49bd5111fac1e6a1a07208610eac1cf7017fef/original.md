```julia
function cochranqMcTest(tables::AbstractVector{Matrix{I}};
            direction::TestDir = Both(),
            switch2rand::Int = max(Int(1e8) ÷ length(𝐘), Int(1e4)),
            nperm::Int = 20_000, 
            seed::Int = 1234, 
            verbose::Bool = true,
            #
            stepdown::Bool = true,
            fwe::Float64 = 0.05,
            threaded::Bool = Threads.nthreads()>=4) 
                where {I <: Int, TestDir <: TestDirection}
```

Multiple comparisons [Cochran Q](https://en.wikipedia.org/wiki/Cochran's_Q_test) by data permutation. 

The Cochran Q test is analogous to the 1-way ANOVA for repeated measures, but takes as input dicothomous  data (zeros and ones). Given $M$ hypotheses, consisting each in $N$ observation units  (e.g., *subjects*, *blocks*, etc.) and $K$ repeated measures (e.g., *treatments*, *time*, etc.),  the null hypotheses have form

$H_0(m): μ_{m1}= \ldots =μ_{mk}, \quad m=1...M$,

where $μ_{mk}$ is the mean of the $k^{th}$ treatment. 

Input `tables` is a vector of $M$ tables of zeros and ones with size $NxK$, where $N$ is the number  of observations and $K$ the repeated measures. See [`cochranqTest`](@ref) for more explanations.

For optional keyword arguments, `direction`, `switch2rand`, `nperm`, `seed`, `verbose`, `stepdown`, `fwe` and `threaded` see [here](@ref "Common kwargs for multiple comparisons tests"). 

*Directional tests, Permutation scheme and number of permutations for exact tests:* as per *univariate version* [`cochranqTest`](@ref)

*Aliases:* `qMcTest`, [`mcNemarMcTest`](@ref)

Return a [MultcompTest](@ref) structure.

*Examples*

```julia
using PermutationTests
tables=[ [1 1 0; 1 0 0; 1 1 1; 1 1 0; 1 0 1; 1 1 0],
        [1 0 0; 1 1 0; 1 1 0; 1 1 1; 1 0 0; 1 0 0],
        [1 0 0; 0 0 1; 1 0 1; 1 1 0; 1 0 1; 1 0 0]];
t=qMcTest(tables) # the test with K>2 can only be bi-directional
```
