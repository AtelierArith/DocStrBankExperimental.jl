```julia
function fisherExactMcTest(<same args and kwargs as `chiSquaredMcTest`>)
```

Actually an alias for [`chiSquaredMcTest`](@ref). It can be used for 2x2 contingency tables. See [`chiSquaredTest`](@ref) for more explanations.

*Univariate version:* [`fisherExactTest`](@ref)

Return a [MultcompTest](@ref) structure.

*Examples*

```julia
using PermutationTests
tables=[[6 1; 2 5], [4 1; 4 5], [5 2; 3 4]];
tR=fisherExactMcTest(tables; direction=Right()) 
# or tR=Χ²Test(tables; direction=Right())
```
