```
Spectral <: EliminationAlgorithm

Spectral(; tol=0.0)
```

スペクトル順序アルゴリズムは、接続されたグラフでのみ機能します。これを使用するには、パッケージ [Laplacians](https://github.com/danspielman/Laplacians.jl) をインポートしてください。

```julia-repl
julia> using CliqueTrees, Laplacians

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

julia> alg = Spectral(; tol=0.001)
Spectral:
    tol: 0.001

julia> treewidth(graph; alg)
4
```

### パラメータ

  * `tol`: 収束のための許容誤差

### 参考文献

  * Barnard, Stephen T., Alex Pothen, and Horst D. Simon. "A spectral algorithm for envelope reduction of sparse matrices." *Proceedings of the 1993 ACM/IEEE Conference on Supercomputing.* 1993.
