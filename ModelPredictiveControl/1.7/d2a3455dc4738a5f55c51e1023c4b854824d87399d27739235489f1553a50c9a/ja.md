```
initstate!(estim::StateEstimator, u, ym, d=[]) -> x̂
```

現在の入力 `u`、測定出力 `ym` および外乱 `d` から `estim.x̂0` 状態を初期化します。

このメソッドは、初期推定値 $\mathbf{x̂}$ の良好な定常状態を見つけようとします。 [`remove_op!`](@ref) で動作点を削除し、[`init_estimate!`](@ref) を呼び出します：

  * `estim.model` が [`LinModel`](@ref) の場合、`u` および `d` 引数を使用して拡張モデルの定常状態を見つけ、`ym` 引数を使用して $\mathbf{ŷ^m}(0) = \mathbf{y^m}(0)$ を強制します。制御アプリケーションの場合、この解はバンプレス手動から自動への移行を生成します。詳細については [`init_estimate!`](@ref) を参照してください。
  * それ以外の場合、`estim.x̂0` は変更されません。手動で変更するには [`setstate!`](@ref) を使用してください。

該当する場合、誤差共分散 `estim.P̂` を `estim.P̂_0` に設定します。

# 例

```jldoctest
julia> estim = SteadyKalmanFilter(LinModel(tf(3, [10, 1]), 0.5), nint_ym=[2], direct=false);

julia> u = [1]; y = [3 - 0.1]; x̂ = round.(initstate!(estim, u, y), digits=3)
3-element Vector{Float64}:
 10.0
  0.0
 -0.1

julia> x̂ ≈ updatestate!(estim, u, y)
true

julia> evaloutput(estim) ≈ y
true
```
