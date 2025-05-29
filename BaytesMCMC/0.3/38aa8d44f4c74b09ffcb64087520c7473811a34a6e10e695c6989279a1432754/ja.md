```julia
mutable struct Proposal{A<:BaytesCore.UpdateBool, T<:AbstractFloat, P<:(AbstractMatrix), C<:(AbstractMatrix), M<:BaytesMCMC.MatrixTune}
```

提案分布コンテナ。

# フィールド

  * `adaption::BaytesCore.UpdateBool`: 現在のイテレーションでの適応が真であるかをチェック
  * `chain::Matrix{T} where T<:AbstractFloat`: 現在のMCMCフェーズにおけるθᵤサンプル、Σ推定に使用
  * `Σ::AbstractMatrix`: 事後共分散の推定
  * `Σ⁻¹ᶜʰᵒˡ::AbstractMatrix`: 逆事後共分散行列Σのコレスキー分解、s.t. Σ⁻¹ᶜʰᵒˡ*Σ⁻¹ᶜʰᵒˡ'=Σ⁻¹。HMC/NUTSサンプラーでのランダムドロー生成に使用。
  * `matrixtune::BaytesMCMC.MatrixTune`: Σ推定のための調整パラメータ
