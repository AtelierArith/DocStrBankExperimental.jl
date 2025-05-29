```
has_simpsons_paradox(df, cause, effect, factor;
    continuous_threshold = 5, cmax = 5, verbose = true)
```

Returns true if the data aggregated by `factor` exhibits Simpson's paradox. Note that the `cause` and `effect` columns will be converted to Int columns if they are not already numeric in type. A continuous data `factor` column (one with `continuous_threshold` or more discrete levels) will be grouped into a at most cmax clusters so as to avoid too many clusters. Prints the regression slope directions for overall data and groups if verbose is true. Example:     df = DataFrame(         treatment = [1, 2, 1, 1, 2, 2],         recovery = [1, 0, 1, 1, 0, 0],         kidney*stone*size = ["small", "small", "large", "small", "large", "large"])     has*simpsons*paradox(df, :treatment, :recovery, :kidney*stone*size)
