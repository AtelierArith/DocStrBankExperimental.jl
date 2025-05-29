スモリャク多項式の勾配を計算するためにマルチスレッドを使用する補間関数を作成します。サンプリングポイント `y` と近似 `plan` を指定します。補間関数を返します。

# シグネチャ

grad = smolyak*gradient*threaded(y,plan)

# 例

```
julia> g,mi = smolyak_grid(chebyshev_extrema,2,2,[1.0 1.0; 0.0 0.0])
julia> y = g[:,1].^0.3.*g[:,2].^0.7
julia> splan = smolyak_plan(chebyshev_extrema,2,2,[1.0 1.0; 0.0 0.0])
julia> grad = smolyak_gradient_threaded(y,splan)
julia> grad([0.37,0.71])
[0.403682  0.525063]
```
