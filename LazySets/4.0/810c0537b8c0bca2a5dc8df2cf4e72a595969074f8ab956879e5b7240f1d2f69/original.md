```
project(X::LazySet, block::AbstractVector{Int}, [::Nothing=nothing],
        [n]::Int=dim(X); [kwargs...])
```

Project a set to a given block by using a concrete linear map.

### Input

  * `X`       – set
  * `block`   – block structure - a vector with the dimensions of interest
  * `nothing` – (default: `nothing`) needed for dispatch
  * `n`       – (optional, default: `dim(X)`) ambient dimension of the set `X`

### Output

A set representing the projection of `X` to block `block`.

### Algorithm

We apply the function `linear_map`.
