```
RCMGL{A} <: EliminationAlgorithm

RCMGL(alg::Algorithm)

RCMGL()
```

[逆カササギ-マッキーアルゴリズム](https://en.wikipedia.org/wiki/Cuthill%E2%80%93McKee_algorithm)。初期頂点はジョージとリウのGPSアルゴリズムの変種を使用して選択されます。

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

julia> alg = RCMGL(QuickSort)
RCMGL:
    Base.Sort.QuickSortAlg()

julia> treewidth(graph; alg)
3
```

### パラメータ

  * `alg`: ソートアルゴリズム

### 参考文献

  * Cuthill, Elizabeth, and James McKee. "スパース対称行列の帯域幅を減少させる。" *1969年第24回全国会議の議事録。* 1969年。
  * George, Alan, and Joseph WH Liu. "擬似周辺ノードファインダーの実装。" *ACM Transactions on Mathematical Software (TOMS)* 5.3 (1979): 284-295.
