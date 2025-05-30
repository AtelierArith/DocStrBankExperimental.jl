```
CompositeRotations{C, A} <: EliminationAlgorithm

CompositeRotations(clique::AbstractVector, alg::EliminationAlgorithm)

CompositeRotations(clique::AbstractVector)
```

与えられたクリークが順序の最後に来るように、排除アルゴリズムを評価します。

```julia-repl
julia> using CliqueTrees

julia> graph = [
           0 1 0 0 0 0 0 0
           1 0 1 0 0 1 0 0
           0 1 0 1 0 1 1 1
           0 0 1 0 0 0 0 0
           0 0 0 0 0 1 1 0
           0 1 1 0 1 0 0 0
           0 0 1 0 1 0 0 1
           0 0 1 0 0 0 1 0
       ];

julia> alg = CompositeRotations([2], MCS())
CompositeRotations{Vector{Int64}, MCS}:
    clique: [2]
    MCS

julia> order, index = permutation(graph; alg);

julia> order # 2は順序の最後の頂点です
8-element Vector{Int64}:
 4
 5
 7
 8
 3
 6
 1
 2
```

### パラメータ

  * `clique`: クリーク
  * `alg`: 排除アルゴリズム

### 参考文献

  * Liu, Joseph WH. "Equivalent sparse matrix reordering by elimination tree rotations." *Siam Journal on Scientific and Statistical Computing* 9.3 (1988): 424-444.
