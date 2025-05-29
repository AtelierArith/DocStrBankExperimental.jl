```julia
# METHOD (2)
function anovaTestRM(yvec::UniDataVec; <same kwargs>)
```

METHOD (1)

Univariate [1-way analysis of variance (ANOVA) for repeated measures](https://en.wikipedia.org/wiki/Repeated_measures_design#Repeated_measures_ANOVA)  by data permutation. Given $K$ repeated measures (e.g., treatments, time, etc.) for each of $N$ observation units  (e.g., subjects, blocks, etc.), the null hypothesis has form

$H_0: μ_1= \ldots =μ_K$,

where $μ_k$ is the mean of the $k^{th}$ treatment. 

`y` is a vector concatenaning the $K$ treatments (treatment 1,..., treatment $K$) for each observation in this order: the $K$ treatments for observation 1, the $K$ treatments for observation 2, ...,  the $K$ treatments for observation $N$. Thus, `y` holds $N \cdot K$ elements. 

`ns` is a julia [named tuple](https://docs.julialang.org/en/v1/manual/types/#Named-Tuple-Types)  with form `(n=N, k=K)` (see examples below).

For optional keyword arguments, `direction`, `equivalent`, `switch2rand`, `nperm`, `seed` and `verbose`,  see [here](@ref "Common kwargs for univariate tests"). 

*Directional tests*

Possible only for $𝐾=2$, in which case the test reduces to a one-sample Student' t-test on the  differences of the two treatments and the test directionality is given by keyword arguement `direction`.  See function [`studentTest1S`](@ref) and its multiple comparisons version [`studentMcTest1S`](@ref). 

*Permutation scheme:* under the null hypothesis, the order of the $K$ measurements bears no meaning. The exchangeability scheme consists then in reordering the $K$ measurements within the $N$ observation units. 

*Number of permutations for exact tests:* there are $K!^N$ possible ways of reordering the $K$ measurements in all $N$ observation units.

**Alias:** `fTestRM`

*Multiple comparisons version:* [anovaMcTestRM](@ref)

Both methods return a [UniTest](@ref) structure.

METHOD (2)

As (1), but `yvec` is a vector of $N$ vectors holding each the $K$ treatments for the $n^{th}$  subject (see examples below).

*Examples*

```julia
# (1)
using PermutationTests
N=6; # number of observation units
K=3; # number of measurements
y = [randn(K) for n=1:N] # some random Gaussian data for example 
t = fTestRM(vcat(y...), (n=N, k=K)) # ANOVA tests are always bi-directional
```

```julia
# Force an approximate test with 5000 random permutations
tapprox = fTestRM(vcat(y...), (n=N, k=K); switch2rand=1, nperm=5000)
```

```julia
# in method (2) only the way the input data is formatted is different 
t2 = fTestRM(y)
println(t.p ≈ t2.p ? "OK" : "error")
```

**Similar tests**

Typically, the input data is real, but can also be of type integer or boolean. For dicothomous data,  with this function one can obtain the permutation-based Cochran Q test for $K>2$ and the permutation-based McNemar test  for $K=2$, but with the ability to give exact p-values. For these two tests the dedicated functions [`cochranqTest`](@ref) and [`mcNemarTest`](@ref) is available.
