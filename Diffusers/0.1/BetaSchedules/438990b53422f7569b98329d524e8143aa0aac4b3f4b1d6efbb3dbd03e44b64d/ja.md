線形ベータスケジュール。

## 入力

  * `T::Integer`: タイムステップの数
  * `β₁::Real=1.0f-4`: 初期 (t=1) のβの値
  * `β₋₁::Real=2.0f-2`: 最終 (t=T) のβの値

## 出力

  * `β::Vector{Real}`: 各タイムステップtにおけるβₜの値

## 参考文献

  * [[2006.11239] Denoising Diffusion Probabilistic Models](https://arxiv.org/abs/2006.11239)
