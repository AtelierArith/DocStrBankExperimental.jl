```
test_slope(xs::Array,
           ys::Array;
           slope::Number = 0,
           intercept::Bool = true
)
```

Make linear regression and return the p value of whether the regression slope     differs from the given slope, given

  * `xs` Array of x, can be NaN
  * `ys` Array of y, can be NaN
  * `slope` Slope to test
  * `intercept` Optional: if true use intercept in the fitting
