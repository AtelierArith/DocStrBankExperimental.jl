```
updatestate!(estim::StateEstimator, u, ym, d=[]) -> x̂next
```

現在の入力 `u`、測定された出力 `ym` および分布 `d` を使用して `estim.x̂0` の推定値を更新します。

この関数は、各離散時間ステップの最後に呼び出す必要があります。 [`remove_op!`](@ref) で動作点を削除し、[`update_estimate!`](@ref) を呼び出し、次の時間ステップの状態推定値 $\mathbf{x̂}_k(k+1)$ を返します。推定が適用可能な場合（`estim.direct == true` の場合）、この関数の前に [`preparestate!`](@ref) を呼び出す必要があります。デフォルトの `direct=true` オプションを持つ [`MovingHorizonEstimator`](@ref) は $\mathbf{x̂}_k(k+1)$ を推定することができないため、返される値は現在の修正された状態 $\mathbf{x̂}_k(k)$ です。

# 例

```jldoctest
julia> kf = SteadyKalmanFilter(LinModel(ss(0.1, 0.5, 1, 0, 4.0))); u = [1]; ym = [0];

julia> preparestate!(kf, ym);

julia> x̂ = updatestate!(kf, u, ym) # x̂[2] は積分器の状態 (nint_ym 引数)
2-element Vector{Float64}:
 0.5
 0.0
```
