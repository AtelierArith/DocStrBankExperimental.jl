```
discretemeasure(
    support::AbstractVector,
    probs::AbstractVector{<:Real}=FillArrays.Fill(inv(length(support)), length(support)),
)
```

Construct a finite discrete probability measure with `support` and corresponding `probabilities`. If the probability vector argument is not passed, then equal probability is assigned to each entry in the support.

# Examples

```julia
using KernelFunctions
# rows correspond to samples
μ = discretemeasure(RowVecs(rand(7,3)), normalize!(rand(10),1))

# columns correspond to samples, each with equal probability
ν = discretemeasure(ColVecs(rand(3,12)))
```

!!! note
    If `support` is a 1D vector, the constructed measure will be sorted, e.g. for `mu = discretemeasure([3, 1, 2],[0.5, 0.2, 0.3])`, then `mu.support` will be `[1, 2, 3]` and `mu.p` will be `[0.2, 0.3, 0.5]`. Also, avoid passing 1D distributions as `RowVecs(rand(3))` or `[[1],[3],[4]]`, since this will be dispatched to the multivariate case instead of the univariate case for which the algorithm is more efficient.


!!! warning
    This function and in particular its return values are not stable and might be changed in future releases.

