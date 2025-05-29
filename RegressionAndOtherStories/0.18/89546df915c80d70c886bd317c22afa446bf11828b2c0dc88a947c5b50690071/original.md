# errorbars_mean

Compute errorbar DataFrame for the means of columns in a DataFrame.

```julia
errorbars_mean(df)
errorbars_mean(df, p)

```

## Required arguments

  * `df`: DataFrame

# `p = [0.055, 0.945]`: Probability bounds

## Result

A DataFrame (with a `parameters` column)

Exported.
