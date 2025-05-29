```
grid([v]; algo=DemmlerReinsch())
```

Specify the grid vector `v` used for [`GridSearch`](@ref). If `v` is not provided, a default grid is used. The default algorithm used for assessing the alternative parameters on the grid is [`DemmlerReinsch`](@ref), which is very fast.
