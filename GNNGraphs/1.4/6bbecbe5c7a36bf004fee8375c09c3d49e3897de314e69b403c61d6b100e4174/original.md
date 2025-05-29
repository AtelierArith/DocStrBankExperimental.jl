```
DataStore([n, data])
DataStore([n,] k1 = x1, k2 = x2, ...)
```

A container for feature arrays. The optional argument `n` enforces that `numobs(x) == n` for each array contained in the datastore.

At construction time, the `data` can be provided as any iterables of pairs of symbols and arrays or as keyword arguments:

```jldoctest
julia> ds = DataStore(3, x = rand(Float32, 2, 3), y = rand(Float32, 3))
DataStore(3) with 2 elements:
  y = 3-element Vector{Float32}
  x = 2×3 Matrix{Float32}

julia> ds = DataStore(3, Dict(:x => rand(Float32, 2, 3), :y => rand(Float32, 3))); # equivalent to above
```

The `DataStore` has an interface similar to both dictionaries and named tuples. Arrays can be accessed and added using either the indexing or the property syntax:

```jldoctest docstr_datastore
julia> ds = DataStore(x = ones(Float32, 2, 3), y = zeros(Float32, 3))
DataStore() with 2 elements:
  y = 3-element Vector{Float32}
  x = 2×3 Matrix{Float32}

julia> ds.x   # same as `ds[:x]`
2×3 Matrix{Float32}:
 1.0  1.0  1.0
 1.0  1.0  1.0

julia> ds.z = zeros(Float32, 3)  # Add new feature array `z`. Same as `ds[:z] = rand(Float32, 3)`
3-element Vector{Float32}:
 0.0
 0.0
 0.0
```

The `DataStore` can be iterated over, and the keys and values can be accessed using `keys(ds)` and `values(ds)`. `map(f, ds)` applies the function `f` to each feature array:

```jldoctest docstr_datastore
julia> ds2 = map(x -> x .+ 1, ds)
DataStore() with 3 elements:
  y = 3-element Vector{Float32}
  z = 3-element Vector{Float32}
  x = 2×3 Matrix{Float32}

julia> ds2.z
3-element Vector{Float32}:
 1.0
 1.0
 1.0
```
