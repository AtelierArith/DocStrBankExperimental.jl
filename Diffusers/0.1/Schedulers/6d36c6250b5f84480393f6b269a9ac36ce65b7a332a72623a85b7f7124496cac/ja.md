拡散プロセスの速度を計算します。

## 入力

  * `scheduler::Scheduler`: 使用するスケジューラ
  * `x₀::AbstractArray`: ノイズを加えるクリーンデータ
  * `ϵ::AbstractArray`: クリーンデータに加えるノイズ
  * `t::AbstractArray`: ノイズに重みを付けるために使用されるタイムステップ

## 出力

  * `vₜ::AbstractArray`: 指定されたタイムステップでの速度

## 参考文献

  * [[2202.00512] Progressive Distillation for Fast Sampling of Diffusion Models](https://arxiv.org/abs/2202.00512) (Ann. D)
