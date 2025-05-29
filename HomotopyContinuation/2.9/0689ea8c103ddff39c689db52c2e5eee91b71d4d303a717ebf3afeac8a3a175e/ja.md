```
multiplicities(vectors; metric = EuclideanNorm(), atol = 1e-14, rtol = 1e-8, kwargs...)
```

`Vector{Vector{Int}}` `v` を返します。`v` の各ベクトル `w` には、`w[i]` と `w[j]` の距離が `max(atol, rtol * metric(0,w[i]))` 以下であるすべてのインデックス `i`,`j` が含まれます。残りの `kwargs` は [`UniquePoints`](@ref) に渡すことができるものです。

```julia-repl
julia> multiplicities([[1,0.5], [1,0.5], [1,1]])
[[1,2]]
```

これは次のように同じです。

```julia
multiplicities([[1,0.5], [1,0.5], [1,1]]; distance=(x,y) -> LinearAlgebra.norm(x-y))
```

グループ作用を使用する例です。

```julia-repl
julia> X = [[1, 2, 3, 4], [2,1,3,4], [1,2,4,3], [2,1,4,3]]
julia> permutation(x) = [x[2], x[1], x[3], x[4]]
julia> m = multiplicities(X, group_action = permutation)
[[1,2], [3,4]]
```
