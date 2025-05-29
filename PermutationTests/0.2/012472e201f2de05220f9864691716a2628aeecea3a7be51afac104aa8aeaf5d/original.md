```julia
function mcNemarTest(same args and kwargs as `cochranqTest`>)
```

Univariate [McNemar test](https://en.wikipedia.org/wiki/McNemar's_test) by data permutation. Alias  for [`cochranqTest`](@ref). It can be used for $2 \cdot 2$ contingency tables.

Notice that [`cochranqTest`](@ref) does not accept data input in the  form of a contingency table. If your data is in the form of a contingency table, here is how you can convert it:

given the contingency table

| a | b |

| c | d |

you will create a vector holding:

  * as many vectors `[0, 1]` as the $b$ frequency.
  * as many vectors `[1, 0]` as the $c$ frequency.

For example, the contingency table

| 1 | 2 |

| 3 | 4 |

will be given as input such as as

```julia
table=[0 1; 0 1; 1 0; 1 0; 1 0]
```

!!! note "Redundant permutations"
    Adding any number of vectors `[0 0]` or `[1 1]` in any combination to the table here above,  yields exactly the same p-value using systematic permutations. Like in the asymptotic McNemar test, these vector correspond to elements `a` and `d` of the  contingency table and have no effect.


*Directional tests*

  * For a right-directional test, $c$ is expected to exceed $b$. If the opposite is true, the test will result in a p-value higher then 0.5.
  * For a left-directional test, $b$ is expected to exceed $c$. If the opposite is true, the test will result in a p-value higher then 0.5.

*Multiple comparisons version:* [`mcNemarMcTest`](@ref)

Return a [UniTest](@ref) structure.

*Examples*

```julia
using PermutationTests
table=[1 0; 1 0; 1 0; 1 0; 0 1]
t=mcNemarTest(table) # by default the test is bi-directional

tR=mcNemarTest(table; direction=Right()) # right-directional test
```
