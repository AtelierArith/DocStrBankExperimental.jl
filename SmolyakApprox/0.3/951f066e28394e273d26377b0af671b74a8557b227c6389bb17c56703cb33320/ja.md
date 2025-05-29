マルチスレッドを使用して、サンプリングポイント `y` と近似 `plan` を与えて補間関数を構築する補間関数を作成します。補間関数を返します。

# シグネチャ

f = smolyak*interp*threaded(y,plan)

# 例

```
julia> g,mi = smolyak_grid(chebyshev_extrema,2,2,[1.0 1.0; 0.0 0.0])
julia> y = g[:,1].^0.3.*g[:,2].^0.7
julia> splan = smolyak_plan(chebyshev_extrema,2,2,[1.0 1.0; 0.0 0.0])
julia> f = smolyak_interp_threaded(y,splan)
julia> f([0.37,0.71])
0.5953026581237828

julia> g,mi = smolyak_grid(clenshaw_curtis_equidistant,2,2,[1.0 1.0; 0.0 0.0])
julia> y = g[:,1].^0.3.*g[:,2].^0.7
julia> splan = smolyak_plan(clenshaw_curtis_equidistant,2,2,[1.0 1.0; 0.0 0.0])
julia> f = smolyak_interp_threaded(y,splan)
julia> f([0.37,0.71])
0.5549321821467206
```
