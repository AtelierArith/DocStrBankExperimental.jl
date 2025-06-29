```
LJRef <: EmpiricHelmholtzModel
LJRef(components;
userlocations = String[],
verbose = false)
```

## 入力パラメータ

  * `sigma`: 単一パラメータ (`Float64`) - 粒子サイズ [Å]
  * `epsilon`: 単一パラメータ (`Float64`) - 分散エネルギー [`K`]
  * `Mw`: 単一パラメータ (`Float64`) - 分子量 `[g/mol]`
  * `k`: ペアパラメータ (`Float64`) (オプション) - `sigma` 混合係数

## モデルパラメータ

  * `sigma`: ペアパラメータ (`Float64`) - 粒子サイズ [m]
  * `epsilon`: ペアパラメータ (`Float64`) - 分散エネルギー [`K`]
  * `Mw`: 単一パラメータ (`Float64`) - 分子量 `[g/mol]`

## 説明

レナード-ジョーンズ参照状態方程式。0.5 < T/Tc < 7 および p/pc = 500 までの圧力で有効。

```
σᵢⱼ = (σᵢ + σⱼ)/2
ϵᵢⱼ = (1-kᵢⱼ)√(ϵⱼϵⱼ)
σ^3 = Σxᵢxⱼσᵢⱼ^3
ϵ = Σxᵢxⱼϵᵢⱼσᵢⱼ^3/σ^3
τᵢ = 1.32ϵᵢ/T
δᵢ = n(Nₐσᵢ^3)/0.31V
a⁰ᵢ(δ,τ) = log(δᵢ) + 1.5log(τᵢ) - 1.515151515τᵢ + 6.262265814
a⁰(δ,τ,z) = ∑xᵢ(a⁰ᵢ + log(xᵢ))
τ = 1.32ϵ/T
δ = n(Nₐσ^3)/0.31V
aʳ(δ,τ)  = aʳ₁+ aʳ₂ + aʳ₃ + aʳ₄
aʳ₁(δ,τ)  = ∑nᵢδ^(dᵢ)τ^(tᵢ), i ∈ 1:6
aʳ₂(δ,τ)  = ∑nᵢexp(-δ^cᵢ)δ^(dᵢ)τ^(tᵢ), i ∈ 7:12
aʳ₃(δ,τ)  = ∑nᵢexp(-ηᵢ(δ - εᵢ)^2 - βᵢ(τ - γᵢ)^2)δ^(dᵢ)τ^(tᵢ), i ∈ 13:23
```

パラメータ `n`,`t`,`d`,`c`,`η`,`β`,`γ`,`ε` はフィッティングによって得られました。

!!! 警告 "複数成分の警告"     元のモデルは単一成分のみを考慮して作成されました。複数成分をサポートするために、VDW 1-fluid 混合則（上記参照）が実装されていますが、テストは行われていません。

## 参考文献

1. Thol, M., Rutkai, G., Köster, A., Lustig, R., Span, R., & Vrabec, J. (2016). レナード-ジョーンズ流体の状態方程式. Journal of physical and chemical reference data, 45(2), 023101. [doi:10.1063/1.4945000](https://doi.org/10.1063/1.4945000)
