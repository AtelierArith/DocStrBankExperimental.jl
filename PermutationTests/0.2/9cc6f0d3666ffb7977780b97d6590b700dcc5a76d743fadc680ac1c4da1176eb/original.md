```julia
function cochranqTest(table::Matrix{I};
            direction::TestDir = Both(),
            equivalent::Bool = true,
            switch2rand::Int = Int(1e8),
            nperm::Int = 20_000, 
            seed::Int = 1234, 
            verbose::Bool = true) where {I <: Int, TestDir <: TestDirection}

```

Univariate [Cochran Q](https://en.wikipedia.org/wiki/Cochran's_Q_test) test by data permutation. The Cochran Q test  is analogous to the 1-way ANOVA for repeated measures, but takes as input dicothomous data (zeros and ones). Given $N$ observation units (e.g., subjects, blocks, etc.) and $K$ repeated measures  (e.g., treatments, time, etc.), the null hypothesis has form

$H_0: μ_1= \ldots =μ_K$,

where $μ_k$ is the mean of the $k^{th}$ measure. 

When $K=2$ the test reduces to the [McNemar test](https://en.wikipedia.org/wiki/McNemar's_test), which is the analogous to the Student's t-test for repeated measures taking as input dicothomous data (zeros and ones). 

Input `table` is a $N \cdot K$ table of zeros and ones, where $N$ is the number of observations and  $K$ the repeated measures. Transposed, one such data would look like

| 1 | 1 | 1 | 1 | 1 | 1 | Measure 1

| 1 | 0 | 1 | 1 | 0 | 1 | Measure 2

| 0 | 0 | 1 | 0 | 1 | 0 | Measure 3

This table shall be given as input such as      `table=[1 1 0; 1 0 0; 1 1 1; 1 1 0; 1 0 1; 1 1 0]`

and internally it will be converted to the appropriate format by function [`table2vec`](@ref).

!!! note "Redundant permutations"
    Adding any number of vectors `[0 0 0]` or `[1 1 1]` in any combination to the table here above,  yields exactly the same p-value using systematic permutations, but increase the number of permutations to be listed. If such vector exist in your data, you can delete them to obatin a faster test.


For optional keyword arguments, `direction`, `equivalent`, `switch2rand`, `nperm`, `seed` and `verbose`,  see [here](@ref "Common kwargs for univariate tests").

In contrast to the [Cochran Q](https://en.wikipedia.org/wiki/Cochran's_Q_test) and  [McNemar](https://en.wikipedia.org/wiki/McNemar's_test) asymptotic tests,  with permutation tests the sample size does not have to be large. Actually, for large sample sizes the Cochran Q and McNemar tests are more efficient, although they do not provide  an exact p-value (an exact test for the case $K=2$ can be derived though). Overall, this permutation test is not very useful when compared to the standard Cochran Q and McNemar tests,  however, its multiple comparison version allows the control of the family-wise error rate by means of data permutation. 

*Directional tests*

Possible only for $𝐾=2$, in which case the test reduces to a MnNemar test  and the test directionality is given by keyword arguement `direction`.  See function [`mcNemarTest`](@ref) and its multiple comparisons version [`mcNemarMcTest`](@ref). 

*Permutation scheme:* the F-statistic of the 1-way ANOVA for repeated measure is an equivalent test-statistic for the  Cochran Q test and the permutation scheme of that ANOVA applies (see [`anovaTestRM`](@ref)). The permutation scheme is the same for tha case of $K=2$ (McNemar test).

*Number of permutations for exact tests:* there are $K!^N$ possible ways of reordering the $K$ measurements in all the $N$ observation units.

*Aliases:* `qTest`, `mcNemarTest`

*Multiple comparisons versions:* [`cochranqMcTest`](@ref), [`mcNemarMcTest`](@ref) 

Return a [UniTest](@ref) structure.

*Examples*

```julia
using PermutationTests
table=[1 1 0; 1 0 0; 1 1 1; 1 1 0; 1 0 1; 1 1 0]
t=qTest(table) # the test is bi-directional
```
