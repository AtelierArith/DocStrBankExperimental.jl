Package: ForecastPlots

```
splot(x, labels; plot = true)
```

Plot a seasonal plot of x based on the parameter `labels`

# Arguments

  * `x`: Regular timed observations
  * `labels`: This parameter accepts Integer, String and Vector values.            - When an Integer the labels are 1:labels.           - When a Vector the sorted labels are specified within.           - When a String it accepts values "month", "day" and "quarter"m, by default the first value of x to fall in "Jan", "Mon" or "Q1", if other initial values are required labels must be specified in a vector.
  * `plot`: When `true` the splot is displayed, otherwise only the seasonal per column matrix is returned.

# Returns

Matrix with seasonal data by column with an optional  plot

# Examples

```julia-repl
splot(rand(120),"month");
splot(rand(120),"quarter");
splot(rand(120),"day"; plot=false)
18×7 Matrix{Union{Missing, Float64}}:
 0.799164   0.214773   0.957464   0.969107   0.5886    0.153288   0.298444
 0.631211   0.539124   0.728887   0.235045   0.398699  0.492781   0.332502
 0.691047   0.473517   0.834303   0.0316447  0.208999  0.231782   0.00797575
```
