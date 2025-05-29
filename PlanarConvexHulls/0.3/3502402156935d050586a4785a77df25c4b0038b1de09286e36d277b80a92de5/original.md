```julia
hrep!(A, b, hull)

```

Return the equivalent halfspace representation of the convex hull, i.e. matrix $A$ and vector $b$ such that the set of points inside the hull is

$$
\left\{ x \mid A x \le b \right\}
$$

This function stores its output in the (mutable) matrix `A` and vector `b`.
