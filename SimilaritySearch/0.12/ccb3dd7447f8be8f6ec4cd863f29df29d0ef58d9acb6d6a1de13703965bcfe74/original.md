```
neardup(idx::AbstractSearchIndex, ctx::AbstractContext, X::AbstractDatabase, ϵ::Real; k::Int=8, blocksize::Int=get_parallel_block(), minbatch=0, filterblocks=true, verbose=true)
neardup(dist::SemiMetric, X::AbstractDatabase, ϵ::Real; kwargs...)
```

Find nearest duplicates in database `X` using the empty index `idx`. The algorithm iteratively try to index elements in `X`, and items being near than `ϵ` to some element in `idx` will be ignored.

The function returns a named tuple `(idx, map, nn, dist)` where:

  * `idx`: it is the index of the non duplicated elements
  * `ctx`: the index's context
  * `map`: a mapping from `|idx|-1` to its positions in `X`
  * `nn`: an array where each element in $x \in X$ points to its covering element (previously indexed element `u` such that $d(u, x_i) \leq ϵ$)
  * `dist`: an array of distance values to each covering element (correspond to each element in `nn`)

# Arguments

  * `idx`: An empty index (i.e., a `SearchGraph`)
  * `X`: The input dataset
  * `ϵ`: Real value to cut, if negative, then ϵ will be computed using the quantile value at 'abs(ϵ)' in a small sample of nearest neighbor distances; the quantile method should be used only for applications that need some vague approximations to `ϵ`

# Keyword arguments

  * `k`: The number of nearest neighbors to retrieve (some algorithms benefit from retrieving larger `k` values)
  * `blocksize`: the number of items processed at the time
  * `minbatch`: argument to control `@batch` macro (see `Polyester` package multithreading)
  * `filterblocks`: if true then it filters neardups inside blocks (see `blocksize` parameter), otherwise, it supposes that blocks are free of neardups (e.g., randomized order).
  * `verbose`: controls the verbosity of the function

# Notes

  * The index `idx` must support incremental construction
  * If you need to customize object insertions, you must wrap the index `idx` and implement your custom methods; it requires valid implementations of the following functions:

      * `searchbatch(idx::AbstractSearchIndex, ctx, queries::AbstractDatabase, knns::Matrix, dists::Matrix)`
      * `distance(idx::AbstractSearchIndex)`
      * `length(idx::AbstractSearchIndex)`
      * `append_items!(idx::AbstractSearchIndex, ctx, items::AbstractDatabase)`
  * You can access the set of elements being 'ϵ-non duplicates (the $ϵ-net$) using `database(idx)` or where `nn[i] == i`
