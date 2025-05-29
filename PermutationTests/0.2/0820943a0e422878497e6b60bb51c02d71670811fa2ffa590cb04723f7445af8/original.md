```julia
# METHOD (2)
function anovaMcTestRM(Yvec::UniDataVec²; <same kwargs>)
```

**METHOD (1)**

Multiple comparison [1-way analysis of variance (ANOVA) for repeated measures](https://en.wikipedia.org/wiki/Repeated_measures_design#Repeated_measures_ANOVA)  by data permutation. Given $M$ hypotheses, each with $K$ repeated measures (e.g., treatments, time, etc.) for each of $N$ observation units  (e.g., subjects, blocks, etc.), the null hypotheses have form

$H_0(m): μ_{m1}= \ldots =μ_{mk}, \quad m=1...M$,

where $μ_{mk}$ is the mean of the $k^{th}$ treatment for the $m^{th}$ hypothesis. 

`Y` is a vector hoding $M$ vectors, each one concatenaning the $K$ treatments (treatment 1,..., treatment $K$)  for each observation for the $m^{th}$ hypothesis in this order: the $K$ treatments for observation 1, the $K$ treatments for observation 2, ...,  the $K$ treatments for observation $N$. Thus, `Y` holds $M$ vectors of $N \cdot K$ elements. 

`ns` is a julia [named tuple](https://docs.julialang.org/en/v1/manual/types/#Named-Tuple-Types)  with form `(n=N, k=K)` (see examples below).

For optional keyword arguments, `direction`, `switch2rand`, `nperm`, `seed`, `verbose`, `stepdown`, `fwe` and `threaded` see [here](@ref "Common kwargs for multiple comparisons tests"). 

*Directional tests, permutation scheme and number of permutations for exact tests:* as per *univariate version* [`anovaTestRM`](@ref)

*Alias:* `fTestMcRM`

Return a [MultcompTest](@ref) structure.

**METHOD (2)**

As (1), but `Yvec` is a vector of $M$ vectors, each one holding $N$ vectors holding each the $K$ treatments for the $n^{th}$  subject (see examples below).

*Examples*

```julia
# method (1)
using PermutationTests
N=6 # number of observation units per treatment
K=3 # number of treatments
M=10 # number of hypotheses
Yvec = [[randn(K) for n=1:N] for m=1:M]; # some random Gaussian data for example 
t = fMcTestRM([vcat(yvec...) for yvec in Yvec], (n=N, k=K)) 
# ANOVA tests are always bi-directional
```

```julia
# Force an approximate test with 5000 random permutations
tapprox = fMcTestRM([vcat(yvec...) for yvec in Yvec], (n=N, k=K); 
            switch2rand=1, nperm=5000)

# in method (2) only the way the input data is formatted is different 
 
t2 = fMcTestRM(Yvec)
println(sum(abs.(t.p - t2.p)) ≈ 0. ? "OK" : "error")
println(sum(abs.(t.obsstat - t2.obsstat)) ≈ 0. ? "OK" : "error")


```

**Similar tests**

See [`anovaTestRM`](@ref)
