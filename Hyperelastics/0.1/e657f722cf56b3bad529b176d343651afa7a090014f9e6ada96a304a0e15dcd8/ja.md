```julia
StrainEnergyDensity(
    ψ::Hyperelastics.AbstractHyperelasticModel{T<:Hyperelastics.PrincipalValueForm},
    F::Array{R, 2},
    p
) -> Any

```

ハイパーエラスティックモデルに基づいてひずみエネルギー密度関数を返します。これは変形勾配 `F` の主ストレッチを計算することに基づいています。固有値は以下の手順で求められます：

$$
C = F^T \cdot F
a = transpose(eigvecs(C))
C^\ast = (U^\ast)^2 = a^T \cdot C \cdot a
\vec{\lambda} = diag(U)
$$

# 引数:

  * `ψ::AbstractHyperelasticModel`: ハイパーエラスティックモデル
  * `F::Matrix`: 変形勾配行列
  * `p`: モデルパラメータ
