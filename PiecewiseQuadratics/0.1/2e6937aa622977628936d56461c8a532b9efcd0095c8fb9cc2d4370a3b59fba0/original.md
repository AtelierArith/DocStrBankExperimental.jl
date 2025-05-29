```
BoundedQuadratic(lb::Real, ub::Real, p::Real, q::Real, r::Real)
```

Represents bounded quadratic function

$$
f(x) = px^2 + qx + r, ∀ x ∈ [lb, ub]
$$

The fields represent:

  * `lb`: Lower bound of the function
  * `ub`: Upper bound of the function
  * `p`: Coefficient of the quadratic term
  * `q`: Coefficient of the linear term
  * `r`: Constant

# Example

```jldoctest
julia> bq = BoundedQuadratic(0., 5., 3., 2., 1.)
BoundedQuadratic: f(x) = 3.00000 x² + 2.00000 x + 1.00000, ∀x ∈ [0.00000, 5.00000]

```
