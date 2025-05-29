```julia
function pointBiSerialMcTest(<same args and kwargs as `studentMcTestIS`>)
```

Actually an alias for [`studentMcTestIS`](@ref).

Run $M$ [point bi-serial correlation tests](https://en.wikipedia.org/wiki/Point-biserial_correlation_coefficient) simultaneously. The correlations are between the $M$ input data vectors $y_1,...,y_M$ given as argument `Y`,  all holding $N=N_1+N_2$ elements, and a vector $x$, internally created, with the first $N_1$ elements equal to `1` and the remaining $N_2$ elements equal to `2`.

If you need to use other values for the dicothomous variable $x$ or a different order for its elements,  use [`correlationMcTest`](@ref) instead. 

The $M$ null hypotheses have form 

$H_0(m): b_{(x,y_m)}=0, \quad m=1...M$,

where $b_{(x,y_m)}$ is the point bi-serial correlation between $y_m$ (the $m^{th}$ input data vectors in `Y`)  and the internally created vector $x$.

*Directional tests, permutation scheme and number of permutations for exact tests:* as per *univariate version* [`pointBiSerialTest`](@ref)

Return a [MultcompTest](@ref) structure.

*Examples*

```julia
using PermutationTests
ns=[4, 6]; # N1=4, N2=6
N=sum(ns); # number of observations

Y = [rand(N) for m=1:M]; # some Gaussian data as example
# implicitly, the point bi serial correlation is between 
# y1,...,yM and x=[1, 1, 1, 1, 2, 2, 2, 2, 2, 2]
t=pointBiSerialMCTest(Y, ns) # by default the test is bi-directional
```

```julia
tR=pointBiSerialMCTest(Y, ns; direction=Right()) # right-directional test
tL=pointBiSerialMCTest(Y, ns; direction=Left()) # left-directional test
```
