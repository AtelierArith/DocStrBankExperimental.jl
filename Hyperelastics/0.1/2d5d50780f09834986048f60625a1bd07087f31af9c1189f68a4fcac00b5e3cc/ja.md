```julia
CauchyStressTensor(
    ψ::Hyperelastics.AbstractHyperelasticModel{T<:Hyperelastics.PrincipalValueForm},
    λ⃗::Array{R, 1},
    p;
    kwargs...
) -> Any

```

ハイパーエラスティックモデル `ψ` のためのコーシー応力テンソルを、主ストレッチ `λ⃗` とパラメータ `p` で返します。

# 引数:

  * `ψ::AbstractHyperelasticModel`: ハイパーエラスティックモデル
  * `λ⃗::Vector`: 主ストレッチのベクトル
  * `p`: モデルパラメータ
  * `ad_type`: 自動微分バックエンド (詳細は `ADTypes.jl` を参照)
