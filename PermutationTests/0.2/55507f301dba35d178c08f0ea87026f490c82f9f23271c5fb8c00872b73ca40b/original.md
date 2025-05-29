```julia
function fisherExactTest(<same args and kwargs as `chiSquaredTest`>)
```

Perform an univariate [Fisher exact test](https://en.wikipedia.org/wiki/Fisher's_exact_test) by data permutation. Alias for [chiSquaredTest](@ref). It can be used for $2 \cdot 2$ contingency tables.  The contingency table in this case has form:

| a | b |

| c | d |

  * For a right-directional test, $a/c$ is expected to exceed $b/d$. If the opposite is true, the test will result in a p-value higehr then 0.5.
  * For a left-directional test, $b/d$ is expected to exceed $a/c$. If the opposite is true, the test will result in a p-value higehr then 0.5.

!!! tip "Nota Bene"
    For $K=2$, any input data matrix gives the same p-value as its transpose.


*Multiple comparisons version:* [fisherExactMcTest](@ref)

Return a [UniTest](@ref) structure.

*Examples*

```julia
using PermutationTests
table=[6 1; 2 5]
t=fisherExactTestTest(table) 
# or t=Χ²Test(table) # bi-directional test
```

```julia
tR=fisherExactTest(table; direction=Right())  # right-directional test
```
