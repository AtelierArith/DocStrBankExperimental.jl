```julia
add_to_dataframe!(df, stats)
add_to_dataframe!(df, stats, pre)
add_to_dataframe!(df, stats, pre, post)

```

Store results from observation type `stats_t` in dataframe `df`. With `pre` and `post` additional data that is not contained in the stats object can be added.
