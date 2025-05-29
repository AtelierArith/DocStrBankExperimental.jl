```julia
# METHOD (2)
function anovaMcTestIS(𝐘vec::UniDataVec²; <same kwargs>)
```

**METHOD (1)**

Multiple comparisons [1-way analysis of variance (ANOVA) for independent samples](https://en.wikipedia.org/wiki/One-way_analysis_of_variance)  by data permutation. 

Run $M$ ANOVAs simultaneously. The Input data is given as a vector `Y` holding $M$ vectors $𝐲1,...,𝐲M$ concatenating all observations, that is, holding each $N=N_1+...+N_K$ observations  for $K>2$ independent samples (groups). The observations are ordered with group 1 first, then group 2,..., finally group K. Note that the group numerosity $N_1,...,N_K$ must be the same for all $M$ hypotheses.  The only check performed is that the first vector in `Y` contains `sum(ns)` elements.

The $M$ null hypotheses have form

$H_0(m): μ_{m1}= \ldots =μ_{mK}, \quad m=1...M$,

where $μ_{mk}$ is the mean of the $k^{th}$ group for the $m^{th}$ hypothesis.

`ns` is a vector of integers holding the group numerosity $N_1,...,N_K$ (see examples below).

For optional keyword arguments, `direction`, `switch2rand`, `nperm`, `seed`, `verbose`, `stepdown`, `fwe` and `threaded` see [here](@ref "Common kwargs for multiple comparisons tests").

Directional tests, permutation scheme and number of permutations for exact tests: as per *univariate version* [`anovaTestIS`](@ref)

*Alias:* `fMcTestIS`

Return a [MultcompTest](@ref) structure.

**METHOD (2)**

As method (1), but input data `Yvec` is a vector holding $M$ vectors of K vectors of  observations for group 1,..., group K. 

*Examples*

```julia
# method (1)
using PermutationTests
ns=[3, 4, 5] # number of observations in group 1, 2 and 3
M=10 # number of hypotheses
Yvec = [[randn(n) for n in ns] for m=1:M]; # some random Gaussian data for example 
t = fMcTestIS([vcat(y...) for y in Yvec], ns) # ANOVA tests are always bi-directional

# Force an approximate test with 5000 random permutations
tapprox = fMcTestIS([vcat(y...) for y in Yvec], ns; switch2rand=1, nperm=5000) 

# in method (2) only the way the input data is formatted is different 
t2 = fMcTestIS(Yvec)
# of course, method (1) and (2) give the same p-values
println(sum(abs.(t.p-t2.p))≈0. ? "OK" : "error") 
```

**Similar tests**

See [`anovaTestIS`](@ref)
