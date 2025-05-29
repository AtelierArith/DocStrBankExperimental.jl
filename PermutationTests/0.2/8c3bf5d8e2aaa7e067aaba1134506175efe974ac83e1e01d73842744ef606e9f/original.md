```julia
function chiSquaredTest(table::Matrix{I};
            direction::TestDir = Both(),
            equivalent::Bool = true,
            switch2rand::Int = Int(1e8),
            nperm::Int = 20_000, 
            seed::Int = 1234, 
            verbose::Bool = true,
            asPearson::Bool = true) where {I <: Int, TestDir <: TestDirection}

```

Univariate [chi-squared](https://en.wikipedia.org/wiki/Chi-squared_test) ($\chi^2$) permutation test  for $2 \cdot K$ contingency tables, where $K$ is ≥2.  The null hypothesis has form 

$H_0: O=E$,

where $O$ and $E$ are the observed and expected frequencies of the contingency table.

`table` is a contingency table given in the form of a matrix of integers. For example, the contingency table

| 0 | 2 | 3 | Failures 

| 3 | 1 | 0 | Successes

will be given as

```julia
table=[0 2 3; 3 1 0]
```

For optional keyword arguments, `direction`, `equivalent`, `switch2rand`, `nperm`, `seed` and `verbose`,  see [here](@ref "Common kwargs for univariate tests").

For $K=2$ this function calls [`studentTestIS`](@ref) and pass to it also argument `asPearson`, otherwise calls [`anovaTestIS`](@ref) and argument `asPearson` is ignored.

In contrast to Pearson's asymptotic $\chi^2$, with permutation tests the sample size does not have to be large. Actually, for large sample sizes Pearson's test is more efficient. For small sample sizes the p-value can be obtained  using all possible permutations, thus being exact and will be the same as the p-value obtained using  the [Fisher exact test](https://en.wikipedia.org/wiki/Fisher%27s_exact_test).

This permutation test is therefore not particularly useful when compared to the standard $\chi^2$ and Fisher exact test,  however, its multiple comparison version allows the control of the family-wise error rate through data permutation. 

*Directional tests*

Possible only for $𝐾=2$, in which case the test reduces to a Fisher exact test  and the test directionality is given by keyword arguement `direction`.  See function [`fisherExactTest`](@ref) and its multiple comparisons version [`fisherExactMcTest`](@ref). 

*Permutation scheme:* the contingency table is converted to $K$ vectors holding each as many observations as the corresponding column sum.  The conversion is operated internally by function [`table2vec`](@ref). The elements of the vectors are as many zeros and ones as the counts of the two cells of the correspondind column. The F-statistic of the 1-way ANOVA for indepedent samples is then an equivalent test-statistic for the  $\chi^2$ and the permutation scheme of that ANOVA applies (see [`anovaTestIS`](@ref)).

*Number of permutations for exact tests:* there are $\frac{N!}{N_1 \cdot\ldots\cdot N_K}$ possible permutations, where $K$ is the number of columns in the contingency table and $N_k$ is the $k^{th}$ column sum.

*Aliases:* `Χ²Test`, [`fisherExactTest`](@ref)

*Multiple comparisons version:* [chiSquaredMcTest](@ref)

Return a [UniTest](@ref) structure.

*Examples*

```julia
using PermutationTests
table=[0 2 2; 3 1 0]
t=Χ²Test(table) # the test is bi-directional
```

```julia
table=[6 1; 2 5]
tR=fisherExactTest(table; direction=Right()) 
# or tR=Χ²Test(table; direction=Right())
```
