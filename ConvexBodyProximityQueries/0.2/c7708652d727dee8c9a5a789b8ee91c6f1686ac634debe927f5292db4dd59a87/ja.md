```
tolerance_verification(p, q, dir, τ; max_iter=100, atol=0.0)
```

凸オブジェクト `p` と `q` が、ある許容範囲内で少なくとも `τ` の許容距離があるかどうかを計算します。問題の空間における初期探索方向 `dir` を提供します。

# 例

```julia-repl
julia> using StaticArrays
julia> p = SMatrix{2,3}([0.0 0.0 1.0; 0.0 2.0 1.0])
julia> q = SMatrix{2,3}([2.0 2.0 3.0; 0.0 2.0 1.0])
julia> dir = SVector{2}(1.0, 0.0)
julia> tolerance_verification(p, q, dir, 0.25)
true
```
