```julia
function studentMcTestRM(<same args and kwargs as `studentMcTest1S`>)
```

Actually an alias for [`studentMcTest1S`](@ref)

In order to run a multiple comparisons t-test for repeated measure, use as data input the vector of  $M$ vectors of differences across the two measurements (or treatments, time, etc.).

Do not change the `refmean` default value. See [`studentMcTest1S`](@ref) for more details.

*Directional tests, permutation scheme and number of permutations for exact tests:* as per [`studentTest1S`](@ref)

*Univariate version:* [`studentTestRM`](@ref)

*Alias:* `tMcTestRM`

Return a [MultcompTest](@ref) structure.

*Examples*

```julia
using PermutationTests
N=10 # number of observation per treatment
M=100 # number of hypotheses

# suppose you have data as
Y1=[randn(N) for m=1:M]; # measurement 1
Y2=[randn(N) for m=1:M]; # measurement 2

# Let us compute the differences as
Y=[y1-y2 for (y1, y2) in zip(Y1, Y2)];
t=tMcTestRM(Y) # by default the test is bi-directional

tR=tMcTestRM(Y; direction=Both()) #  right-directional test
# if test tR is significant for some hypotheses, 
# for these hypotheses the mean of measurement 1 
# exceeds the mean of measurement 2.
```
