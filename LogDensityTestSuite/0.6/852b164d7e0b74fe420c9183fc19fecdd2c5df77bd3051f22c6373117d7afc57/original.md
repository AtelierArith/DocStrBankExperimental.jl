```julia
print_ascii_plot(
    io,
    ubc;
    canvas_width,
    p_colname,
    bin_colname,
    α,
    count_colname,
    padding,
    ess_correction
)

```

Print an ASCII plot to `io` with statistics from the given univariate bin counts. When the first argument is a `String`, return the output as a string instead of printing.

# Keyword arguments

  * `canvas_width`: width of the canvas for the plot
  * `p_colname`: column name for p-values (the actual value printed is `-log10(p)`)
  * `bin_colname`: column name for bin indices
  * `count_colname`: column name for counts
  * `α`: two markers (with `(` and `)` are placed at the quantiles `α` and `1-α`
  * `padding`: enlargement factor for canvas

When `ess_correction = true` (the default), the standard deviation is calculated using the the effective sample size.
