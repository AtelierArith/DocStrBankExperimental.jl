```
LCVMRule{γ} <: LCVMRuleModel

LCVMRule(components;
activity = Wilson,
userlocations = String[],
activity_userlocations = String[],
verbose::Bool=false)
```

## 入力パラメータ

なし

## 入力モデル

  * `activity`: アクティビティモデル

## 説明

VidalとMichaelsenの線形結合 (LCVM) 混合ルール

```
bᵢⱼ = (1 - lᵢⱼ)(bᵢ + bⱼ)/2
b̄ = ∑bᵢⱼxᵢxⱼ
c̄ = ∑cᵢxᵢ
ᾱᵢ  = aᵢαᵢ/bᵢRT
ċ = -q₁*Σᾱᵢxᵢ - q₂*Σᾱᵢxᵢ^2 - gᴱ/RT - ∑log(bᵢᵢ/b̄)
ā = b̄RT(-1.827[gᴱ/RT - 0.3∑log(bᵢᵢ/b̄)] + Σᾱᵢxᵢ)
```

## モデル構築の例

```
# デフォルトデータベースを使用
mixing = LCVMRule(["water","carbon dioxide"]) #デフォルト: Wilsonアクティビティ係数。
mixing = LCVMRule(["water","carbon dioxide"],activity = NRTL) #別のアクティビティ係数モデルを渡す。
mixing = LCVMRule([("ethane",["CH3" => 2]),("butane",["CH2" => 2,"CH3" => 2])],activity = UNIFAC) #GCアクティビティ係数モデルを渡す。

# 事前構築されたモデルを渡す

act_model = NRTL(["water","ethanol"],userlocations = (a = [0.0 3.458; -0.801 0.0],b = [0.0 -586.1; 246.2 0.0], c = [0.0 0.3; 0.3 0.0]))
mixing = LCVMRule(["water","ethanol"],activity = act_model)

# ユーザー提供のパラメータを使用

# ファイルまたはフォルダを渡す
mixing = LCVMRule(["water","ethanol"]; activity = NRTL, activity_userlocations = ["path/to/my/db","nrtl_ge.csv"])

# パラメータを直接渡す
mixing = LCVMRule(["water","ethanol"];
                activity = NRTL,
                userlocations = (a = [0.0 3.458; -0.801 0.0],
                    b = [0.0 -586.1; 246.2 0.0],
                    c = [0.0 0.3; 0.3 0.0])
                )
```

## 参考文献

1. Boukouvalas, C., Spiliotis, N., Coutsikos, P., Tzouvaras, N., & Tassios, D. (1994). LCVMモデルによる蒸気-液平衡の予測: 元のUNIFACと結合されたVidalとMichelsenの混合ルールの線形結合。Fluid Phase Equilibria, 92, 75–106. [doi:10.1016/0378-3812(94)80043-x](https://doi.org/10.1016/0378-3812(94)80043-x)
