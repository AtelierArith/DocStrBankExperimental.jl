```
NonLinMPC(estim::StateEstimator; <キーワード引数>)
```

カスタム状態推定器 `estim` を使用して `NonLinMPC` を構築します。

# 例

```jldoctest
julia> model = NonLinModel((x,u,_,_)->0.5x+u, (x,_,_)->2x, 10.0, 1, 1, 1, solver=nothing);

julia> estim = UnscentedKalmanFilter(model, σQint_ym=[0.05]);

julia> mpc = NonLinMPC(estim, Hp=20, Hc=1, Cwt=1e6)
NonLinMPC コントローラー、サンプル時間 Ts = 10.0 s、Ipopt オプティマイザー、UnscentedKalmanFilter 推定器、および:
 20 予測ステップ Hp
  1 制御ステップ Hc
  1 スラック変数 ϵ (制御制約)
  1 操作入力 u (0 統合状態)
  2 推定状態 x̂
  1 測定出力 ym (1 統合状態)
  0 測定されていない出力 yu
  0 測定された外乱 d
```
