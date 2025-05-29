```
smooth(gks::GaussianKernelSmoother, bandwidth, xeval; rtol=atol>0 ? 0 : 1e-3, atol=0)
```

与えられた `bandwidth` と `xeval` に対してガウスカーネルスムーザーを評価します。点 `x₀` におけるスムーズ関数 `f` の値は `f(x₀) := ∑ᵢyᵢwᵢ / ∑ᵢwᵢ` で与えられ、ここで `wᵢ := exp(-(x₀-xᵢ)²/2bandwidth²)` です。

結果の精度は `rtol` と `atol` によって制御されます。下限と上限 `lb≤f(x₀)≤ub` は、`isapprox(lb,ub;rtol=rtol,atol=atol)` まで徐々に改善されます。

# 例

```julia-repl
julia> g = GaussianKernelSmoother([0.0,1.0],[2.0,4.0]);
julia> smooth.(g, 1, [0.1, 0.5, 0.9])
3-element Array{Float64,1}:
 2.802624679775096
 3.0
 3.197375320224904
```

`GaussianKernelSmoother` や `density` も参照してください。
