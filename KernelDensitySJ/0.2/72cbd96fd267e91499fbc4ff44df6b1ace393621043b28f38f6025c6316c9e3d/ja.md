```
smooth(x, y, bandwidth, xeval; leafSize=10, rtol=atol>0 ? 0 : 1e-3, atol=0)
```

座標 `x` と値 `y` のデータポイントのセットに対して、指定された `bandwidth` で、`xeval` の座標でガウスカーネルスムーザーを評価します。スムーズ関数 `f` の値は `x₀` で次のように与えられます：`f(x₀) := ∑ᵢyᵢwᵢ / ∑ᵢwᵢ`、ここで `wᵢ := exp(-(x₀-xᵢ)²/2bandwidth²)` です。

結果の精度は `rtol` と `atol` によって制御されます。下限と上限 `lb≤f(x₀)≤ub` は、`isapprox(lb,ub;rtol=rtol,atol=atol)` まで徐々に改善されます。

`xeval` および/または `bandwidth` に対してベクトル/行列引数で `smooth` を一度呼び出す方が、`smooth` を複数回呼び出すよりもはるかに効率的です。

# 例

```julia-repl
julia> smooth([0.0,1.0], [2.0,4.0], 1.0, [0.1, 0.5, 0.9])
3-element Array{Float64,1}:
 2.802624679775096
 3.0
 3.197375320224904
```

`GaussianKernelSmoother`、`density` も参照してください。
