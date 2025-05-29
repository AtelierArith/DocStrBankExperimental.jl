```
diff(S::Spline, [op::Derivative = Derivative(1)]) -> Spline
```

Same as `op * S`.

Returns `N`-th derivative of spline `S` as a new spline.
