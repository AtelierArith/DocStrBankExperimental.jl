```
pairwise(dist::StringDistance, xs::AbstractVector, ys::AbstractVector = xs; preprocess = true)
```

Compute distances between all pairs of elements in `xs`  and `ys` according to the `StringDistance` `dist`. Returns a matrix R such that `R[i, j]` corrresponds to the distance between `xs[i]` and `ys[j]`.

Set `preprocess` to false if no preprocessing should be used.

Both symmetric and asymmetric versions are available.

### Examples

```julia-repl
julia> using StringDistances
julia> iter = ["New York", "Princeton"]
julia> pairwise(Levenshtein(), iter)
2×2 Array{Float64,2}:
 0.0  9.0
 9.0  0.0
julia> iter2 = ["San Francisco"]
julia> pairwise(Levenshtein(), iter, iter2)
2×1 Array{Float64,2}:
 12.0
 10.0
```
