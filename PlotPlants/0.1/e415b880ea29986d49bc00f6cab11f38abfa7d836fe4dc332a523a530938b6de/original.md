```
plot_line_regress!(
            ax::PyObject,
            xs::Array,
            ys::Array;
            linestyle::String = "-",
            intercept::Bool = true,
            interval::Bool = false,
            color::String = "red",
            alpha::Number = 0.3
)
```

Plor linear regression and confidence interval on the axis, given

  * `ax` Given axis
  * `xs` Array of x
  * `ys` Array of y
  * `linestyle` Optional. Line style for the regression curve ("-" by default)
  * `intercept` Optional: if true, fit the data with an intercept
  * `interval` Optional: if true, plot the confidence interval of fitted y
  * `color` Color the fitted curve
  * `alpha` Transparency of the confidence interval (same color as curve)
