```
PenelouxTranslation <: PenelouxTranslationModel

PenelouxTranslation(components;
userlocations = String[],
verbose::Bool=false)
```

## 入力パラメータ

  * `Vc`: 単一パラメータ (`Float64`) - 臨界体積 `[m³/mol]`

## モデルパラメータ

  * `Vc`: 単一パラメータ (`Float64`) - 臨界体積 `[m³/mol]`
  * `v_shift`: 単一パラメータ (`Float64`) - 体積シフト `[m³/mol]`

## 説明

ペネルー翻訳モデル（キュービック用）:

```
V = V₀ + mixing_rule(cᵢ)
cᵢ = -0.252*RTcᵢ/Pcᵢ*(1.5448Zcᵢ - 0.4024)
Zcᵢ = Pcᵢ*Vcᵢ/(RTcᵢ)
```

## モデル構築の例

```
# デフォルトデータベースを使用
translation = PenelouxTranslation("water") #単一入力
translation = PenelouxTranslation(["water","ethanol"]) #複数成分

# ユーザー提供のパラメータを使用

# ファイルまたはフォルダを渡す
translation = PenelouxTranslation(["neon","hydrogen"]; userlocations = ["path/to/my/db","critical/Vc.csv"])

# パラメータを直接渡す
translation = PenelouxTranslation(["neon","hydrogen"];userlocations = (;Vc = [4.25e-5, 6.43e-5]))
```

## 参考文献

1. Péneloux A, Rauzy E, Fréze R. (1982) A consistent correction for Redlich‐Kwong‐Soave volumes. Fluid Phase Equilibria 1, 8(1), 7–23. [doi:10.1016/0378-3812(82)80002-2](https://doi.org/10.1016/0378-3812(82)80002-2)
