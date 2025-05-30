```
preparestate!(estim::StateEstimator, ym, d=[]) -> x̂
```

測定出力 `ym` と分布 `d` を用いて、現在の時間ステップの `estim.x̂0` 推定を準備します。

この関数は、各離散時間ステップの開始時に呼び出されるべきです。その動作は、`estim` が現在/フィルタ（1.）または遅延/予測（2.）の [`StateEstimator`](@ref) であるかどうかによって異なります：

1. `estim.direct` が `true` の場合、[`remove_op!`](@ref) を使用して動作点を削除し、[`correct_estimate!`](@ref) を呼び出し、修正された状態推定 $\mathbf{x̂}_k(k)$ を返します。
2. それ以外の場合は、何もしないで現在の最良推定 $\mathbf{x̂}_{k-1}(k)$ を返します。

# 例

```jldoctest
julia> estim2 = SteadyKalmanFilter(LinModel(ss(0.1, 0.5, 1, 0, 4)), nint_ym=0, direct=true);

julia> x̂ = round.(preparestate!(estim2, [1]), digits=3)
1-element Vector{Float64}:
 0.01

julia> estim1 = SteadyKalmanFilter(LinModel(ss(0.1, 0.5, 1, 0, 4)), nint_ym=0, direct=false);

julia> x̂ = preparestate!(estim1, [1])
1-element Vector{Float64}:
 0.0
```
