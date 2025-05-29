```
RackettTranslation <: RackettTranslationModel

RackettTranslation(components;
userlocations = String[],
verbose::Bool=false)
```

## 入力パラメータ

  * `Vc`: 単一パラメータ (`Float64`) - 臨界体積 `[m³/mol]`

## モデルパラメータ

  * `Vc`: 単一パラメータ (`Float64`) - 臨界体積 `[m³/mol]`
  * `v_shift`: 単一パラメータ (`Float64`) - 体積シフト `[m³/mol]`

## 説明

Rackett Translationモデルの立方体用:

```
V = V₀ + mixing_rule(cᵢ)
cᵢ = 0.40768*RTcᵢ/Pcᵢ*(0.29441-Zcᵢ)
Zcᵢ = Pcᵢ*Vcᵢ/(RTcᵢ)
```

## モデル構築の例

```
# デフォルトデータベースを使用
translation = RackettTranslation("water") #単一入力
translation = RackettTranslation(["water","ethanol"]) #複数成分

# ユーザー提供のパラメータを使用

# ファイルまたはフォルダを渡す
translation = RackettTranslation(["neon","hydrogen"]; userlocations = ["path/to/my/db","critical/Vc.csv"])

# パラメータを直接渡す
translation = RackettTranslation(["neon","hydrogen"];userlocations = (;Vc = [4.25e-5, 6.43e-5]))
```

## 参考文献

1. Rackett, H. G. (1970). Equation of state for saturated liquids. Journal of Chemical and Engineering Data, 15(4), 514–517. [doi:10.1021/je60047a012](https://doi.org/10.1021/je60047a012)
