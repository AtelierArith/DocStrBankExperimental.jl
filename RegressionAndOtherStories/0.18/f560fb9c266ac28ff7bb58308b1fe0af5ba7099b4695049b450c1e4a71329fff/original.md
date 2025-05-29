# errorbars_draws

Compute errorbar DataFrame for the draws (columns in a DataFrame).

```julia
errorbars_draws(df)
errorbars_draws(df, p)

```

## Required arguments

  * `df`: DataFrame

# `p = [0.055, 0.945]`: Probability bounds

## Result

A DataFrame (with a `parameters` column)

Exported.
