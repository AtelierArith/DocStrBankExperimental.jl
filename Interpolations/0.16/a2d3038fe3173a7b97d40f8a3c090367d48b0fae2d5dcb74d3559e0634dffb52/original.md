```
Quadratic(bc::BoundaryCondition)
```

Indicate that the corresponding axis should use quadratic interpolation.

# Extended help

Assuming uniform knots with spacing 1, the `i`th piece of quadratic spline implemented here is defined as follows:

```
y_i(x) = cm p(x-i) + c q(x) + cp p(1-(x-i))
```

where

```
p(δx) = (δx - 1)^2 / 2
q(δx) = 3/4 - δx^2
```

and the values for `cX` for `X ∈ {m,_,p}` are the pre-filtered coefficients.

For future reference, this expands to the following polynomial:

```
y_i(x) = cm * 1/2 * (x-i-1)^2 + c * (3/4 - x + i)^2 + cp * 1/2 * (x-i)^2
```

When we derive boundary conditions we will use derivatives `y_1'(x-1)` and `y_1''(x-1)`
