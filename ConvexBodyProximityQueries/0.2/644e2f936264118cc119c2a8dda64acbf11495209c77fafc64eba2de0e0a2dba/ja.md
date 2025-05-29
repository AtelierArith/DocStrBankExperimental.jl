```
minimum_distance(p, q, dir; max_iter=100, atol=0.0)
```

凸オブジェクト `p` と `q` の間の最小分離距離を、ある許容範囲内で計算します。問題の空間における初期探索方向 `dir` を提供してください。

# 例

```julia-repl
julia> using StaticArrays
julia> p = SMatrix{2,3}([0.0 0.0 1.0; 0.0 2.0 1.0])
julia> q = SMatrix{2,3}([2.0 2.0 3.0; 0.0 2.0 1.0])
julia> dir = SVector{2}(1.0, 0.0)
julia> minimum_distance(p, q, dir)
1.0
```
