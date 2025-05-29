```
midcor(X, Y; c=9)
```

Compute the correlation between two variables using the midvariance and midcovariances.

$$
\frac{s_{xy}}{\sqrt{s_{xx} \cdot s_{yy}}}
$$

where $s_{xx},s_{yy}$ are the midvariances of each vector, and $s_{xy}$ is the midcovariance of the two vectors.

# Examples

```jldoctest
julia> X = 10 .* randn(rng, 1000, 2) .+ 50;


julia> midcor(X[:, 1], X[:, 2])
-0.010827077678217934
```

# References

1. [Wikipedia](https://en.wikipedia.org/wiki/Biweight_midcorrelation)
2. [NIST: Biweight midcorrelation](https://www.itl.nist.gov/div898/software/dataplot/refman2/auxillar/biwmidcr.htm)

# See Also

[`midvar`](@ref), [`midcov`](@ref), [`scale`](@ref)
