The functional form of the ContinuousTransition node is given by: y ~ Normal(K(a) * x, W⁻¹)

This node transforms an m-dimensional vector x into an n-dimensional vector y via a linear (or nonlinear) transformation with a `n×m`-dimensional matrix `A` that is constructed from a vector `a` via a transformation K(a). ContinuousTransition node is primarily used in two regimes:

# When no structure on A is specified:

```julia
transformation = a -> reshape(a, 2, 2)
...
a ~ MvNormalMeanCovariance(zeros(2), Diagonal(ones(2)))
y ~ ContinuousTransition(x, a, W) where {meta = CTMeta(transformation)}
...
```

# When some structure if A is known:

```julia
transformation = a -> [cos(a[1]) -sin(a[1]); sin(a[1]) cos(a[1])]
...
a ~ MvNormalMeanCovariance(zeros(1), Diagonal(ones(1)))
y ~ ContinuousTransition(x, a, W) where {meta = CTMeta(transformation)}
...
```

To construct the matrix `A`, the elements of `a` are reshaped into `A` according to the transformation function provided in the meta. If you intend to use univariate Gaussian distributions, use it as a vector of length `1``, e.g.`a ~ MvNormalMeanCovariance([0.0], [1.;])`.

Check ContinuousTransitionMeta for more details on how to specify the transformation function that **must** return a matrix.

```julia
y ~ ContinuousTransition(x, a, W) where {meta = ContinuousTransitionMeta(transformation)}
```

Interfaces:

1. y - n-dimensional output of the ContinuousTransition node.
2. x - m-dimensional input of the ContinuousTransition node.
3. a - any-dimensional vector that casts into the matrix `A`.
4. W - `n×n`-dimensional precision matrix used to soften the transition and perform variational message passing.

Note that you can set W to a fixed value or put a prior on it to control the amount of jitter.

The ContinuousTransition node support two factorizations:

1. Mean-field factorization:

```julia
@constraints begin
    q(y, x, a, W) = q(y)q(x)q(a)q(W)
end
```

2. Structured factorization:

```julia
@constraints begin
    q(y, x, a, W) = q(y, x)q(a)q(W)
end
```
