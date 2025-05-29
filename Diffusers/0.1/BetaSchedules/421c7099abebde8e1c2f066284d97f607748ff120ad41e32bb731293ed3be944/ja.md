コサインベータスケジュール。

## 入力

  * `T::Int`: タイムステップの数
  * `βₘₐₓ::Real=0.999f0`: βの最大値
  * `ϵ::Real=1.0f-3`: ゼロ除算を避けるために使用される小さな値

## 出力

  * `β::Vector{Real}`: 各タイムステップtにおけるβₜの値

## 参考文献

  * [[2102.09672] 改良されたデノイジング拡散確率モデル](https://arxiv.org/abs/2102.09672)
  * [github:openai/improved-diffusion](https://github.com/openai/improved-diffusion/blob/783b6740edb79fdb7d063250db2c51cc9545dcd1/improved_diffusion/gaussian_diffusion.py#L36)
