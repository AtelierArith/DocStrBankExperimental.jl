```
line_regress(
            xs::Array,
            ys::Array;
            intercept::Bool = true,
            sorting::Bool = true
)
```

Make linear regression and return the fitted results, given

  * `xs` Array of x, can be NaN
  * `ys` Array of y, can be NaN
  * `intercept` Optional: if true use intercept in the fitting
  * `sorting` Optional: if true, sort the values
