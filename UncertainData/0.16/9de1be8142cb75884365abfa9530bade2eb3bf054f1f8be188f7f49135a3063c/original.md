```
example_constraints(X::AbstractUncertainIndexValueDataset, 
    d_xinds = Uniform(0.5, 1.1), d_yinds = Uniform(0.9, 1.7))
```

Generate a set of random sampling constraints that can be used to constrain  the indices and values of an uncertain index-value dataset `X`. These are  generated as follows: 

  * `constraints_inds = TruncateStd(rand(d_xinds))`
  * `constraints_vals = [TruncateQuantiles(0.5 - rand(d_xvals), 0.5 + rand(d_xvals)) for i = 1:length(X)];`

Returns the tuple (constraints*inds, constraints*vals).
