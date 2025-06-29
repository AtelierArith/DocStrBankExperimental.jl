```
linear_combination(X::LazySet, Y::LazySet)
```

Compute the linear combination of two sets.

### Input

  * `X` – set
  * `Y` – set

### Output

A set representing the linear combination of `X` and `Y`.

### Notes

The linear combination of two sets $X$ and $Y$ is defined as

$$
    \left\{\frac{1}{2}(1+λ)x + \frac{1}{2}(1-λ)y \mid x ∈ X, y ∈ Y, λ ∈ [-1, 1]\right\}.
$$

If $X$ and $Y$ are convex, their linear combination is identical with the convex hull of their union $X ∪ Y$.
