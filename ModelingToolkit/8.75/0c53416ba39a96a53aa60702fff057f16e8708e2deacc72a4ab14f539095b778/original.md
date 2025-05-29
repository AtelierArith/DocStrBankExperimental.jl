```julia
add_accumulations(sys, vars)

```

Add accumulation variables for `vars`. `vars` is a vector of pairs in the form of

```julia
[cumulative_var1 => x + y, cumulative_var2 => x^2]
```

Then, cumulative variables `cumulative_var1` and `cumulative_var2` that computes the cumulative `x + y` and `x^2` would be added to `sys`.
