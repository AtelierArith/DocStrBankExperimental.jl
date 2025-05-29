# link

Compute the link function for standardized variables.

```julia
link(dfa, vars, xrange)

```

### Required arguments

  * `df::DataFrame`                      : Chain samples converted to a DataFrame
  * `vars::Vector{Symbol}`               : Variables in DataFrame (2 variables)
  * `xrange::range`                      : Range over which link values are computed

### Optional arguments

  * `xbar::Float64`                      : Mean value of observed predictor
  * `ybar::Float64`                      : Mean value of observed outcome (requires xbar argument)

### Return values

  * `result`                             : Vector of link values
