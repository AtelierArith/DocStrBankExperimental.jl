```
RCMMD{A} <: EliminationAlgorithm

RCMMD(alg::Algorithm)

RCMMD()
```

[逆カサリル・マッキーアルゴリズム](https://en.wikipedia.org/wiki/Cuthill%E2%80%93McKee_algorithm)。初期頂点は最小次数ヒューリスティックを使用して選択されます。

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

julia> alg = RCMMD(QuickSort)
RCMMD:
    Base.Sort.QuickSortAlg()

julia> treewidth(graph; alg)
3
```

### パラメータ

  * `alg`: ソートアルゴリズム

### 参考文献

  * Cuthill, Elizabeth, and James McKee. "Reducing the bandwidth of sparse symmetric matrices." *Proceedings of the 1969 24th National Conference.* 1969.
