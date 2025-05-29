```
Cubic(bc::BoundaryCondition)
```

Indicate that the corresponding axis should use cubic interpolation.

# Extended help

Assuming uniform knots with spacing 1, the `i`th piece of cubic spline implemented here is defined as follows.

```
y_i(x) = cm p(x-i) + c q(x-i) + cp q(1- (x-i)) + cpp p(1 - (x-i))
```

where

```
p(δx) = 1/6 * (1-δx)^3
q(δx) = 2/3 - δx^2 + 1/2 δx^3
```

and the values `cX` for `X ∈ {m, _, p, pp}` are the pre-filtered coefficients.

For future reference, this expands out to the following polynomial:

```
y_i(x) = 1/6 cm (1+i-x)^3 + c (2/3 - (x-i)^2 + 1/2 (x-i)^3) +
         cp (2/3 - (1+i-x)^2 + 1/2 (1+i-x)^3) + 1/6 cpp (x-i)^3
```

When we derive boundary conditions we will use derivatives `y_0'(x)` and `y_0''(x)`
