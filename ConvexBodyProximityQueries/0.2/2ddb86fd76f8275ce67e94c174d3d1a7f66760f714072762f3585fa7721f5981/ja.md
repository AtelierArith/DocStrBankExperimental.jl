```
closest_points(p, q, dir; max_iter=100, atol=0.0)
```

凸オブジェクト `p` と `q` の間の最も近い点を計算します。これらがある許容範囲内で衝突していない場合に限ります。問題の空間における初期探索方向 `dir` を提供します。

結果は、各オブジェクトの最も近い2点のStaticArraysを含むタプル型で返されます。

# 例

```julia-repl
julia> using StaticArrays
julia> p = SMatrix{2,3}([0.0 0.0 1.0; 0.0 2.0 1.0])
julia> q = SMatrix{2,3}([2.0 2.0 3.0; 0.0 2.0 1.0])
julia> dir = SVector{2}(1.0, 0.0)
julia> closest_points(p, q, dir)
([1.0, 1.0], [2.0, 1.0])
```
