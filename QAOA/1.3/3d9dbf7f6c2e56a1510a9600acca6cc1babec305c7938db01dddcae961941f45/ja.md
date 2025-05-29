```
evolve_fluctuations(problem::Problem, τ::Real, β::Vector{<:Real}, γ::Vector{<:Real})
```

### 入力

  * `problem::Problem`: 最適化問題を定義する `Problem` インスタンス。
  * `τ::Real`: 考慮されるアニーリングスケジュールの時間ステップ。
  * `β::Vector{<:Real}`: 対応する QAOA ドライバーパラメータのベクトル。
  * `γ::Vector{<:Real}`: 対応する QAOA 問題パラメータのベクトル。

### 出力

  * ガウスの変動の動力学を特徴づけるリャプノフ指数。
