```
UMRRule{γ} <: UMRRuleModel

UMRRule(components;
activity = UNIFAC,
userlocations = String[],
activity_userlocations = String[],
verbose::Bool=false)
```

## 入力パラメータ

なし

## 入力モデル

  * `activity`: 活動モデル

## 説明

普遍混合則ペング・ロビンソン [`UMRPR`](@ref) 状態方程式によって使用される混合則。

```
aᵢⱼ = √(aᵢaⱼ)(1 - kᵢⱼ)
bᵢⱼ = (1 - lᵢⱼ)((√bᵢ +√bⱼ)/2)^2
b̄ = ∑bᵢⱼxᵢxⱼ
c̄ = ∑cᵢxᵢ
ā = b̄RT(∑[xᵢaᵢᵢαᵢ/(RTbᵢᵢ)] - [gᴱ/RT]/0.53)

## モデル構築の例
```

# 注意: このモデルはUNIFAC活動モデル専用に使用されることを意図しています。

# デフォルトデータベースを使用する

mixing = VTPRRule(["water","carbon dioxide"]) #デフォルト: UNIFAC活動係数。 mixing = VTPRRule(["water","carbon dioxide"],activity = NRTL) #別の活動係数モデルを渡す mixing = VTPRRule([("ethane",["CH3" => 2]),("butane",["CH2" => 2,"CH3" => 2])],activity = ogUNIFAC) #GC活動係数モデルを渡す。

# 事前構築されたモデルを渡す

act*model = NRTL(["water","ethanol"],userlocations = (a = [0.0 3.458; -0.801 0.0],b = [0.0 -586.1; 246.2 0.0], c = [0.0 0.3; 0.3 0.0])) mixing = VTPRRule(["water","ethanol"],activity = act*model)

# ユーザー提供のパラメータを使用する

# ファイルまたはフォルダを渡す

mixing = VTPRRule(["water","ethanol"]; activity = NRTL, activity*userlocations = ["path/to/my/db","nrtl*ge.csv"])

# パラメータを直接渡す

mixing = VTPRRule(["water","ethanol"];                 activity = NRTL,                 userlocations = (a = [0.0 3.458; -0.801 0.0],                     b = [0.0 -586.1; 246.2 0.0],                     c = [0.0 0.3; 0.3 0.0])                 )

```
