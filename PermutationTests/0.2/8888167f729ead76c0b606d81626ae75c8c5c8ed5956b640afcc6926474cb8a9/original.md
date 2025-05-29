```julia
# METHOD (3)
function studentTestIS(y1::UniData, y2::UniData; <same kwargs>)
```

**METHOD (1)**

Univariate [Student's t-test for independent samples](https://en.wikipedia.org/wiki/Student's_t-test#Independent_(unpaired)_samples)  by data permutation. Given $N=N1+N_2$ observations in two groups,  the null hypothesis has form

$H_0: μ_1=μ_2$,

where $μ_1$ and $μ_1$ are the mean for group 1 and group 2, respectively. 

For a bi-directional test, this t-test is equivalent to a 1-way ANOVA for two independent samples. However, in contrast to the ANOVA, it can be directional. 

`y` is a vector concatenaning the vector of observations in the two groups. Thus, it holds $N$ elements.

`ns` is a vector of integers holding the group numerosity (see examples below).

For optional keyword arguments, `direction`, `equivalent`, `switch2rand`, `nperm`, `seed` and `verbose`,  see [here](@ref "Common kwargs for univariate tests"). 

If `asPearson` is true (default), the test is run as an equivalent version of a Pearson correlation test. This is not faster in general for exact univariate tests, since the t-test needs  less permutations, but is in general advantageous for approximate tests (see the [benchmarks](@ref "Benchmarks")). If your need to perform exact tests, you may want to set `asPearson` to false.

!!! note "nota"
    If `asPearson` is true, the `.stat` field of the test result will actually be `CrossProd()`, as the data will be standardized before running the test. See [`correlationTest`](@ref).


*Directional tests*

  * For a right-directional test, $μ_1$ is expected to exceed $μ_2$. If the opposite is true, the test will result in a p-value higehr then 0.5.
  * For a left-directional test, $μ_2$ is expected to exceed $μ_1$. If the opposite is true, the test will result a p-value higehr then 0.5.

*Permutation scheme:* under the null hypothesis, the group membership of the observations bears no meaning. The exchangeability scheme consists then in reassigning the $N$ observations in the two groups  respecting the original group numerosity. 

*Number of permutations for exact tests:* there are $\frac{N!}{N_1 \cdot N_2}$ possible reassigments  of the $N$ observations in the two groups.

*Aliases:* `tTestIS`, [`pointBiSerialTest`](@ref)

*Multiple comparisons version:* [`studentMcTestIS`](@ref)

Return a [UniTest](@ref) structure.

**METHOD (2)**

As (1), but `yvec` is a vector of 2-vectors of observations for group 1 and group 2 (see examples below).

**METHOD (3)**

As (1), but the observations are given separatedly for the two groups as two vectors `y1` and `y2` (see examples below).

*Examples*

```julia
# (1)
using PermutationTests
ns=[4, 5]; # number of observations in group 1 and group 2 (N1 and N2)
y=[randn(n) for n∈ns]; # some Gaussian data as example
t = tTestIS(vcat(y...), ns) # by default the test is bi-directional

# with a bi-directional test, t is equivalent to a 1-way ANOVA for independent samples
tanova= fTestIS(vcat(y...), ns) 
println(t.p ≈ tanova.p ? "OK" : "error")

# do not run it using the CrossProd test statistic
tcor = tTestIS(vcat(y...), ns; asPearson=false) 

# Force an approximate test with 10000 random permutations
tapprox = fTestIS(vcat(y...), ns; switch2rand=1, nperm=10000) 

tR=tTestIS(vcat(y...), ns; direction=Right()) # right-directional test
tL=tTestIS(vcat(y...), ns; direction=Left()) # left-directional test

# in method (2) only the way the input data is formatted is different 
t2 = tTestIS(y)
println(t.p ≈ t2.p ? "OK" : "error")

# in method (3) also, only the way the input data is formatted is different 
t3 = tTestIS(y[1], y[2])
println(t.p ≈ t3.p ? "OK" : "error")

```

**Similar tests**

Typically, the input data is real, but can also be of type integer or boolean. 

For dicothomous data, with this function one can obtain the same p-value as the one given by the  Fisher exact test, however in this case it is more convenient to use the [`fisherExactTest`](@ref) function,  since it accepts contingency tables as input. 

This function can also be used to perform a permutation-based point-biserial correlation test. See the dedicated function [`pointBiSerialTest`](@ref). 
