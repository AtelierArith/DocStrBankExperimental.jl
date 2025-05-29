```julia
# METHOD (2)
function anovaTestIS(yvec::UniDataVec; <same kwargs>)
```

**METHOD (1)**

Univariate [1-way analysis of variance (ANOVA) for independent samples](https://en.wikipedia.org/wiki/One-way_analysis_of_variance)  by data permutation.  Given $N=N1+...+N_K$ observations in $K$ groups, the null hypothesis has form

$H_0: μ_1= \ldots =μ_K$,

where $μ_k$ is the mean of the $k^{th}$ group. 

`y` is a vector concatenaning the vector of observations in each group, in the natural order. Thus, it holds $N$ elements. 

`ns` is a vector of integers holding the group numerosity (see examples below).

For optional keyword arguments, `direction`, `equivalent`, `switch2rand`, `nperm`, `seed` and `verbose`,  see [here](@ref "Common kwargs for univariate tests"). 

*Directional tests*

Possible only for $𝐾=2$, in which case the test reduces to a Student' t-test for independent samples and the test directionality is given by keyword arguement `direction`.  See function [`studentTestIS`](@ref) and its multiple comparisons version [`studentMcTestIS`](@ref). 

*Permutation scheme:* under the null hypothesis, the group membership of the observations bears no meaning. The exchangeability scheme consists then in reassigning the $N$ observations in the $K$ groups  respecting the original group numerosity. 

*Number of permutations for exact tests:* there are $\frac{N!}{N_1 \cdot \ldots \cdot N_K}$ possible ways  of reassigning the $N$ observations in the $K$ groups.

**Alias:** `fTestIS`

*Multiple comparisons version:* [anovaMcTestIS](@ref)

Both methods return a [UniTest](@ref) structure.

**METHOD (2)**

As (1), but `yvec` is a vector of K vectors of observations, of for each group.

*Examples*

```julia
# (1)
using PermutationTests
ns=[4, 5, 6] # number of observations in group 1, 2 and 3
yvec = [randn(n) for n in ns] # some random Gaussian data for example 
t = fTestIS(vcat(yvec...), ns) # ANOVA tests are always bi-directional
```

```julia
# Force an approximate test with 5000 random permutations
tapprox = fTestIS(vcat(yvec...), ns; switch2rand=1, nperm=5000) 
```

```julia
# in method (2) only the way the input data is formatted is different 
t2 = fTestIS(yvec)
println(t.p ≈ t2.p ? "OK" : "error")
```

**Similar tests**

Typically, for ANOVA the input data is real, but can also be of type integer or boolean. For dicothomous data,  with this function one can obtain a permutation-based version of the [Χ² test](https://en.wikipedia.org/wiki/Chi-squared_test)  for $K \cdot 2$ contingency tables, which has the ability to give exact p-values.  For $2 \cdot 2$ contingency tables it yields exactly the same p-value of the [Fisher exact test](https://en.wikipedia.org/wiki/Fisher's_exact_test), which is also exact, as the name suggests. In these cases it is more convenient to use the [chiSquaredTest](@ref) and [fisherExactTest](@ref) functions though,  which accept contingency tables as data input. 
