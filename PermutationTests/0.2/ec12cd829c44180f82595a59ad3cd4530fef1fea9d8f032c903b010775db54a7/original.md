```julia
function ∑∑of²(x::UniData)
```

Compute the sum and sum of squares of the elements in `x` in one pass and return them as a 2-tuple.

*Examples*

```julia
using PermutationTests
x=randn(10)
s, s² = ∑∑of²(x)
```
