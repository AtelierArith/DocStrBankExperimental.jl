```julia
StrainEnergyDensity(
    ψ::Hyperelastics.AbstractHyperelasticModel{T},
    _::Array{R, 1},
    p
) -> Any

```

ハイパーエラスティックモデル `ψ` の主ストレッチ `λ⃗` とパラメータ `p` に対するひずみエネルギー密度を返します。

# 引数:

  * `ψ::AbstractHyperelasticModel`: ハイパーエラスティックモデル
  * `λ⃗::Vector`: 主ストレッチのベクトル
  * `p`: モデルパラメータ
