```
mean_and_var(f::FiniteGP)
```

Compute both `mean(f)` and the diagonal elements of `cov(f)`.

Sometimes more efficient than computing them separately, particularly for posteriors.

# Examples

```jldoctest
julia> fx = GP(SqExponentialKernel())(range(-3.0, 3.0; length=10), 0.1);

julia> mean_and_var(fx) == (mean(fx), var(fx))
true
```
