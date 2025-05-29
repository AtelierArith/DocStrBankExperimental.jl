```julia
function studentTestRM(<same args and kwargs as `studentTest1S`>)
```

Univariate [t-test for repeated measures](https://en.wikipedia.org/wiki/Paired_difference_test) by data permutation. Actually an alias for [`studentTest1S`](@ref).

In order to run a t-test for repeated measure, use as data input the vector of differences across measurements.

Do not change the `refmean` default value. See [`studentTest1S`](@ref) for more details.

**Alias:** `tTestRM`

*Multiple comparisons version:* [`studentMcTestRM`](@ref)

Return a [UniTest](@ref) structure.

*Examples*

```julia
using PermutationTests
y1=randn(10) # measurement 1
y2=randn(10) # measurement 2
t=tTestRM(y1.-y2) #  # by default the test is bi-directional

tR=tTestRM(y1.-y2; direction=Both()) #  right-directional test
# if test tR is significant, the mean of measurement 1 exceeds the mean of measurement 2.
```
