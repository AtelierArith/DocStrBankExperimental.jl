```julia
function pointBiSerialTest(<same args and kwargs as `studentTestIS`>)
```

Actually an alias for [`studentTestIS`](@ref).

Univariate [point bi-serial correlation test](https://en.wikipedia.org/wiki/Point-biserial_correlation_coefficient)  by data permutation. The correlation is between an input vector `y` of $N=N_1+N_2$ elements and a vector  $x$, internally created, with the first $N_1$ elements equal to `1` and the remaining $N_2$ elements equal to `2`. If you need to use other values for the dicothomous variable $x$ or a different order for its elements,  use [`correlationTest`](@ref) instead. 

The null hypothesis has form 

$H_0: b_{(x,y)}=0$,

where $b_{(x,y)}$ is the point bi-serial correlation between input data vectors `y` and the internally created vector $x$.

Directional tests, permutation scheme and number of permutations for exact tests: as per [`studentTestIS`](@ref)

*Multiple comparisons version:* [`pointBiSerialMcTest`](@ref)

Return a [UniTest](@ref) structure.

*Examples*

```julia
using PermutationTests
ns=[4, 6] # number of observations in group 1 and group 2 (N1 and N2)
N=sum(ns) # total number of observations

y = rand(N) # some Gaussian data as example
# implicitly, the point bi serial correlation is 
# between y and x=[1, 1, 1, 1, 2, 2, 2, 2, 2, 2]
t=pointBiSerialTest(y, ns) # by default the test is bi-directional

tR=pointBiSerialTest(y, ns; direction=Right()) # right-directional test
tL=pointBiSerialTest(y, ns; direction=Left()) # left-directional test
```
