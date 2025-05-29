Smolyak多項式のヘッセ行列を計算するための補間関数を、サンプリングポイント`y`と近似`plan`を与えて作成します。補間関数を返します。

# シグネチャ

hess = smolyak_hessian(y,plan)

# 例

```
julia> g,mi = smolyak_grid(chebyshev_extrema,2,2,[1.0 1.0; 0.0 0.0])
julia> y = g[:,1].^0.3.*g[:,2].^0.7
julia> splan = smolyak_plan(chebyshev_extrema,2,2,[1.0 1.0; 0.0 0.0])
julia> hess = smolyak_hessian(y,splan)
julia> hess([0.37,0.71])
[-2.53475  1.06753
  1.06753  0.199234]
```
