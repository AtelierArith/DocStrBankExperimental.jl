```julia
SecondPiolaKirchoffStressTensor(
    ψ::Hyperelastics.AbstractHyperelasticModel{T<:Hyperelastics.PrincipalValueForm},
    λ⃗::Array{R, 1},
    p;
    ad_type,
    kwargs...
) -> Any

```

ハイパーエラスティックモデル `ψ` のための第二PK応力テンソルを、主ストレッチ `λ⃗` とパラメータ `p` で返します。

# 引数:

  * `ψ::AbstractHyperelasticModel`: ハイパーエラスティックモデル
  * `λ⃗::Vector`: 主ストレッチのベクトル
  * `p`: モデルパラメータ
  * `ad_type`: 自動微分バックエンド (詳細は `ADTypes.jl` を参照)
