```
vall([p=identity,] A::AbstractArray, dims=:)
```

Determine whether predicate `p` returns true for all elements over the given `dims`. If `p` is omitted, test whether all values along the given `dims` are `true` (in which case `A` should be `AbstractArray{Bool}`).

# Usage Recommendation

If `A` is reasonably small, `vall` may be faster than `all`; however, as the size of `A` grows, the probability of all element returning `false` inevitably increases (it is repeated Bernoulli sampling, thus, even with a very small success probability,  a large number of tries makes may yield a scenario where the `break` of `all` wins out). Consequently, the probability of individual elements being `true` should determine choice – if one suspects a reasonable success probability, then `all` may be preferable, depending on the size `A`. More testing is needed to determine potential breakpoints.

# Additional Notes

This function suffers from the same issue as `vfindmax` and friends – reductions which include the first dimension with max masks are not yet supported by LoopVectorization. Notably, this function still works as intended for any reduction which does not involve the first dimension.
