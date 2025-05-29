```julia
# METHOD (3)
function studentMcTestIS(X::UniDataVec, Y::UniDataVec; <same kwargs>)
```

**METHOD (1)**

Multiple comparisons [Student's t-test for independent samples](https://en.wikipedia.org/wiki/Student's_t-test#Independent_(unpaired)_samples)  by data permutation. 

Run $M$ t-tests simultaneously. Given $M$ hypotheses with $N=N_1+N_2$ observations for two groups each,  the $M$ null hypotheses have form

$H_0(m): μ_{m1}=μ_{m2}, \quad m=1...M$,

where $μ_{m1}$ and $μ_{m2}$ are the mean of group 1 and group 2, respectively, for the $m^{th}$hypothesis. 

For a bi-directional test, this t-test is equivalent to the 1-way ANOVA for two independent samples. However, in contrast to the ANOVA, it can be directional. 

`ns` is a vector of integers holding the group numerosity $N_1, N_2$ (see examples below).

For optional keyword arguments, `direction`, `switch2rand`, `nperm`, `seed`, `verbose`, `stepdown`, `fwe` and `threaded` see [here](@ref "Common kwargs for multiple comparisons tests"). 

If `asPearson` is true(default), the test is run as an equivalent version of a Pearson correlation test. This is in general advantageous for multiple comparison tests, especially if approximate (see the [benchmarks](@ref "Benchmarks")). If you seek best performance for exact tests, benchmark the speed of the test with `asPearson` set to true and to false to see what version is faster for your data. 

!!! note "nota"
    If `asPearson` is true, the `.stat` field of the test result will actually be `CrossProd()`, as the data will be standardized before running the test. See [`correlationTest`](@ref).


*Directional tests, permutation scheme and number of permutations for exact tests:* as per *univariate version* [`studentTestIS`](@ref)

*Aliases:* `tTestMcIS`, [`pointBiSerialMcTest`](@ref)

Return a [MultcompTest](@ref) structure.

**METHOD (2)**

As method (1), but input data `Yvec` is a vector containing $M$ pairs of vector of arbitrary length,  holding in the natural order the data corresponding to the $m^{th}$ hypothesis for group 1 and group 2, respectively.

**METHOD (3)**

As method (1), but input data `X` and `Y` holds $M$ vectors of observations each, `X` corresponding to data  for group 1 and `Y` corresponding to data for group 2.  The $M$ vectors in `X` must have all the same length ($N_1$), so must the $M$ vectors in `Y` ($N_2$). 

*Examples*

```julia
# (1)
using PermutationTests
M=100 # number of hypotheses
ns=[4, 5] # number of observations in group 1 and group 2 (N1 and N2)
N=sum(ns) # total number of observations
Yvec = [[randn(n) for n in ns] for m=1:M]; # some random Gaussian data for example 
Y=[vcat(yvec...) for yvec in Yvec];
t = tMcTestIS(Y, ns) # by default the test is bi-directional

# Force an approximate test with 10000 random permutations
tapprox = tMcTestIS(Y, ns; switch2rand=1, nperm=10000) 
tR=tMcTestIS(Y, ns; direction=Right()) # right-directional test
tL=tMcTestIS(Y, ns; direction=Left()) # left-directional test

# with a bi-directional test, t is equivalent to a 1-way ANOVA for independent samples
tanova= fMcTestIS(Y, ns) 
println(sum(abs.(t.p - tanova.p)) ≈ 0. ? "OK" : "error")

# do not run it using the CrossProd test statistic
tcor = tMcTestIS(Y, ns; asPearson=false) 

# in method (2) only the way the input data is formatted is different 
t2 = tMcTestIS(Yvec)
println(sum(abs.(t.p - t2.p)) ≈ 0. ? "OK" : "error")

# in method (3) also, only the way the input data is formatted is different 
t3 = tMcTestIS([Yvec[m][1] for m=1:M], [Yvec[m][2] for m=1:M])
println(sum(abs.(t.p - t3.p)) ≈ 0. ? "OK" : "error")
```

**Similar tests**

See [`studentTest1S`](@ref)
