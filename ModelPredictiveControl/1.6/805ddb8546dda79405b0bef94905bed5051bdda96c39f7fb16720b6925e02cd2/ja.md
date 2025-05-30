```
LinMPC(estim::StateEstimator; <キーワード引数>)
```

カスタム状態推定器 `estim` を使用して `LinMPC` を構築します。

`estim.model` は [`LinModel`](@ref) でなければなりません。そうでない場合は、[`NonLinMPC`](@ref) が必要です。

# 例

```jldoctest
julia> estim = KalmanFilter(LinModel([tf(3, [30, 1]); tf(-2, [5, 1])], 4), i_ym=[2]);

julia> mpc = LinMPC(estim, Mwt=[0, 1], Nwt=[0.5], Hp=30, Hc=1)
LinMPC コントローラー、サンプル時間 Ts = 4.0 s、OSQP オプティマイザー、KalmanFilter 推定器、および:
 30 予測ステップ Hp
  1 制御ステップ Hc
  1 スラック変数 ϵ (制御制約)
  1 操作入力 u (0 統合状態)
  3 推定状態 x̂
  1 測定出力 ym (1 統合状態)
  1 未測定出力 yu
  0 測定外乱 d
```
