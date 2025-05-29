```
TableDistance(; normalize=true, weights=nothing)
```

Distance between rows of Tables.jl tables.

## Options

  * `normalize` - whether or not to normalize the columns               of the tables before computing distances               (default to `true`)
  * `weights`   - dictionary with weights for each column               (default to uniform weights)

## Examples

```julia
julia> pairwise(TableDistance(), table₁, table₂)
```
