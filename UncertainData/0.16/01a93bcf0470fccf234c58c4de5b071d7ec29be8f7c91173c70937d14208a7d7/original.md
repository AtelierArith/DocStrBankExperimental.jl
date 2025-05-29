```
example_constraints(X::AbstractUncertainIndexValueDataset, 
    Y::AbstractUncertainIndexValueDataset;
    d_xinds = Uniform(0.5, 1.1), d_yinds = Uniform(0.9, 1.7),
    d_xvals = Uniform(0.05, 0.15), d_yvals = Uniform(0.3, 0.4))
```

Generate a set of random sampling constraints that can be used to constrain  the indices and values of two uncertain index-value datasets `X` and `Y`.  The constraints are generated as follows: 

  * `constraints_inds_x = TruncateStd(rand(d_xinds))`
  * `constraints_inds_x = TruncateStd(rand(d_yinds))`
  * `constraints_vals_x = [TruncateQuantiles(0.5 - rand(d_xvals), 0.5 + rand(d_xvals)) for i = 1:length(X)]`
  * `constraints_vals_x = [TruncateQuantiles(0.5 - rand(d_yvals), 0.5 + rand(d_yvals)) for i = 1:length(Y)]`

Returns the tuple of tuples `((constraints_inds_x, constraints_vals_x), (constraints_inds_y, constraints_vals_y))`
