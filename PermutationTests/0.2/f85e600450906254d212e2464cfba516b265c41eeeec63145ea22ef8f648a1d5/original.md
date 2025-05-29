```julia
function chiSquaredMcTest(tables::AbstractVector{Matrix{I}};
            direction::TestDir = Both(),
            switch2rand::Int = max(Int(1e8) ÷ length(𝐘), Int(1e4)), 
            nperm::Int = 20_000, 
            seed::Int = 1234, 
            verbose::Bool = true,            
            #
            stepdown::Bool = true,
            fwe::Float64 = 0.05,
            threaded::Bool = Threads.nthreads()>=4,
            asPearson::Bool = true) 
                    where {I <: Int, TestDir <: TestDirection}
```

Multiple comparisons [chi-squared](https://en.wikipedia.org/wiki/Chi-squared_test) ($\chi^2$) permutation test  for $2 \cdot K$ contingency tables, where $K$ is ≥2.  It tests simultaneously $M$ contingency tables, which must all have same dimension and same column sums.

The $M$ null hypotheses have form 

$H_0(m): O_m=E_m$, \quad m=1...M``,

where $O_m$ and $E_m$ are the observed and expected frequencies of the $m^{th}$contingency table.

`tables` is a vector of $M$ contingency tables. See [`chiSquaredTest`](@ref) for more explanations.

For optional keyword arguments, `direction`, `switch2rand`, `nperm`, `seed`, `verbose`, `stepdown`, `fwe` and `threaded` see [here](@ref "Common kwargs for multiple comparisons tests").

For $K=2$ this function calls [`studentMcTestIS`](@ref) and pass to it also argument `asPearson`, otherwise calls [`anovaMcTestIS`](@ref) and argument `asPearson` is ignored.

*Directional tests, permutation scheme and number of permutations for exact tests:* as per *univariate version* [`chiSquaredTest`](@ref)

*Aliases:* `Χ²McTest`, [`fisherExactMcTest`](@ref)

Return a [MultcompTest] structure.

!!! warning
    For $K>2$, permutations of dicothomous tables may yield a null "sum of squares within",  thus an infinite *F* statistic for the ANOVA. In this case the `.nulldistr` field of the  returned structure will contain some julia `Inf` elements. This does not apply for the univariate  version of the test ([`chiSquaredTest`](@ref)), as in this case an equivalent statistic for the  ANOVA is used (see [Statistic](@ref)) and those statistics can never go to infinity.


*Examples*

```julia
using PermutationTests
tables=[[3 3 2; 0 0 1], [1 2 2; 2 1 1], [3 1 2; 0 2 1]];
t=Χ²McTest(tables) # the test is bi-directional

tables=[[6 1; 2 5], [4 1; 4 5], [5 2; 3 4]]
tR=fisherExactMcTest(tables; direction=Right()) 
# or tR=Χ²Test(tables; direction=Right())

# do not use PearsonR statistic
tR_=fisherExactMcTest(tables; direction=Right(), asPearson=false) 

```
