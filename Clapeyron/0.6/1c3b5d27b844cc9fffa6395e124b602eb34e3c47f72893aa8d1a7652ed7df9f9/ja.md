```
HelmAct::MultiFluid
HelmAct(components;
    pure_userlocations = String[],
    activity = PSRKUNIFAC,
    activity_userlocations = String[],
    estimate_pure = false,
    coolprop_userlocations = false,
    Rgas = R̄,
    reference_state = nothing,
    verbose = verbose)
```

## 入力パラメータ

  * CoolProp JSON 純流体ファイル

## 入力モデル

  * `activity`: 活動モデル。

## 説明

ヘルムホルツ + 活動 (HelmAct) モデルを作成します：

```
aᵣ = ∑xᵢaᵣᵢ(δ,τ) + Δa
Δa = gᴱᵣ/RT - log(1+bρ)/log(1+bρref) * ∑xᵢ(aᵣᵢ(δref,τ) - aᵣᵢ(δrefᵢ,τᵢ))
τᵢ = Tcᵢ/T
δref = ρref/ρr
δrefᵢ = ρrefᵢ/ρcᵢ
b = 1/1.17ρref
```

ここで `gᴱᵣ` は活動モデルから得られる余剰ギブズ自由エネルギーの残余部分です。

## 参考文献

1. Jäger, A., Breitkopf, C., & Richter, M. (2021). The representation of cross second virial coefficients by multifluid mixture models and other equations of state. Industrial & Engineering Chemistry Research, 60(25), 9286–9295. [doi:10.1021/acs.iecr.1c01186](https://doi.org/10.1021/acs.iecr.1c01186)
