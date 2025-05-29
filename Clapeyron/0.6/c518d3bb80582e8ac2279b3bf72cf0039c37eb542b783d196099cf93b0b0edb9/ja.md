```
ConstantTranslation <: ConstantTranslationModel
ConstantTranslation(components;
userlocations = String[],
verbose::Bool=false)
```

## 入力パラメータ

  * `v_shift`: 単一パラメータ (`Float64`) - 体積シフト `[m³/mol]`

## 説明

定数翻訳モデル（キュービック）:

```
V = V₀ + mixing_rule(cᵢ)
```

ここで `cᵢ` は定数です。デフォルトではパラメータはなく、体積シフトはユーザーが提供する必要があります。

## モデル構築の例

```
# ユーザー提供のパラメータを使用

# ファイルまたはフォルダを渡す
translation = ConstantTranslation(["neon","hydrogen"]; userlocations = ["path/to/my/db","properties/critical.csv"])

# パラメータを直接渡す
translation = ConstantTranslation(["neon","hydrogen"];userlocations = (;Vc = [4.25e-5, 6.43e-5]))
```
