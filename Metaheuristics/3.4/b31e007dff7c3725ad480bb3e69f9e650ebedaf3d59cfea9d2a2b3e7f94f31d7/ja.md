```
情報構造
```

`Information` は、メタヒューリスティックを早期に停止させるために真の最適解を保存するために使用できます。

プロパティ：

  * `f_optimum` 知られている最小値。
  * `x_optimum` 知られている最小化点。

`Options` が提供されている場合、`optimize` は `|f(x) - f(x_optimum)| < Options.f_tol` または `‖ x - x_optimum ‖ < Options.x_tol` (ユークリッド距離) のときに停止します。

# 例

精度 `1e-3` で最小値の近似を求める場合 (|f(x) - f(x*)| < 1e-3)、`Information` を使用できます。

```jldoctest
julia> f(x) = sum(x.^2)
f (generic function with 1 method)

julia> bounds = [  -10.0 -10 -10; # 下限
                    10.0  10 10 ] # 上限
2×3 Array{Float64,2}:
 -10.0  -10.0  -10.0
  10.0   10.0   10.0

julia> information = Information(f_optimum = 0.0)
Information(0.0, Float64[])

julia> options = Options(f_tol = 1e-3)
Options(0.0, 0.001, 0.0, 0.0, 1000.0, 0.0, 0.0, 0, false, true, false, :minimize)

julia> state = optimize(f, bounds, ECA(information=information, options=options))
+=========== RESULT ==========+
| Iter.: 22
| f(x) = 0.000650243
| solution.x = [0.022811671589729583, 0.007052331140376011, -0.008951836265056107]
| f calls: 474
| Total time: 0.0106 s
+============================+
```
