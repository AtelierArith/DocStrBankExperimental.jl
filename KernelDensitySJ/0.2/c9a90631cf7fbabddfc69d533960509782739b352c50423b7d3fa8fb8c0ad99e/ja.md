```
density(x, bandwidth, xeval; leafSize=10, rtol=atol>1e-20 ? 0 : 1e-3, atol=1e-20)
```

座標 `x` のデータポイントのセットに対するガウスカーネルスムーザーの密度を、指定された `bandwidth` で `xeval` の座標で評価します。密度 `g` の値は `g(x₀) := C∑ᵢexp(-(x₀-xᵢ)²/2bandwidth²)` で与えられ、ここで `C` は `g` が確率密度関数であることを保証する定数です。

結果の精度は `rtol` と `atol` によって制御されます。下限と上限 `lb≤f(x₀)≤ub` は、`isapprox(lb,ub;rtol=rtol,atol=atol)` まで徐々に改善されます。

`xeval` および/または `bandwidth` に対してベクトル/行列引数で `density` を一度呼び出す方が、`density` を複数回呼び出すよりもはるかに効率的です。

# 例

```julia-repl
julia> density([0.0,1.0], 1.0, [0.1, 0.5, 0.9])
3-element Array{Float64,1}:
 1.6619892900511566
 1.764993805169191
 1.6619892900511566
```

`smooth`、`GaussianKernelSmoother` も参照してください。
