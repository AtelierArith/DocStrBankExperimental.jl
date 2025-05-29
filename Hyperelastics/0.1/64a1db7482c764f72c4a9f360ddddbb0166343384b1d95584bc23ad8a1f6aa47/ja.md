```julia
SecondPiolaKirchoffStressTensor(
    ψ::Hyperelastics.AbstractHyperelasticModel{T<:Hyperelastics.PrincipalValueForm},
    F::Array{R, 2},
    p;
    kwargs...
) -> Any

```

ハイパーエラスティックモデル `ψ` のための第二PK応力テンソルを、変形勾配 `F` とパラメータ `p` で返します。

# 引数:

  * `ψ::AbstractHyperelasticModel`: ハイパーエラスティックモデル
  * `F::Matrix`: 変形勾配行列
  * `p`: モデルパラメータ
  * `ad_type`: 自動微分バックエンド (詳細は `ADTypes.jl` を参照)
