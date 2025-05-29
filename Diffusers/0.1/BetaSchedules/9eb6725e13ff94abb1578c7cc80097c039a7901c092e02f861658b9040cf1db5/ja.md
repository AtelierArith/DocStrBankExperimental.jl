スケーリングされた線形ベータスケジュール。

## 入力

  * `T::Int`: タイムステップの数
  * `β₁::Real=1.0f-4`: βの初期値
  * `β₋₁::Real=2.0f-2`: βの最終値

## 出力

  * `β::Vector{Real}`: 各タイムステップtにおけるβₜの値

## 参考文献

  * [[2006.11239] Denoising Diffusion Probabilistic Models](https://arxiv.org/abs/2006.11239)
