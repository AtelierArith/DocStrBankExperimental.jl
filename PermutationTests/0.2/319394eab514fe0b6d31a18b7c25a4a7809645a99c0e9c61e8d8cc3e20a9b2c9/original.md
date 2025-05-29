```julia
function mcNemarMcTest(same args and kwargs as `cochranqMcTest`>)
```

Actually an alias for [cochranqMcTest)(@ref).

Run $M$ McNemar test simultaneously.

Input `tables` is a vector of $M$ tables of zeros and ones with size $Nx2$, where $N$ is the number  of observations and $2$ the number of repeated measures. See [`cochranqTest`](@ref) for more explanations.

*Univariate version:* [`mcNemarTest`](@ref)

Return a [MultcompTest](@ref) structure.

*Examples*

```julia
using PermutationTests
tables=[[1 1; 1 0; 1 0; 0 0; 1 0; 1 0],
        [1 0; 1 1; 1 0; 0 1; 0 0; 1 0],
        [0 1; 0 0; 1 0; 1 0; 1 0; 1 1]];
t=mcNemarMcTest(tables) # by default the test is bi-directional

tR=mcNemarMcTest(tables; direction=Right()) # right-directional test
```
