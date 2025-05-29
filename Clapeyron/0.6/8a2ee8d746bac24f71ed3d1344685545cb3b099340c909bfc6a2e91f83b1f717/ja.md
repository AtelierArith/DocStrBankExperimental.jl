```
gErRule{γ} <: gErRuleModel

gErRule(components;
activity = NRTL,
userlocations = String[],
activity_userlocations = String[],
verbose::Bool=false)
```

## 入力パラメータ

なし

## 入力モデル

  * `activity`: 活動モデル

## 説明

活動係数モデルの残差部分を使用する混合ルール：

```
bᵢⱼ = ( (bᵢ^(2/3) + bⱼ^(2/3)) / 2 )^(3/2)
b̄ = ∑bᵢⱼxᵢxⱼ
c̄ = ∑cᵢxᵢ
ā/b̄ = b̄RT*(∑xᵢaᵢ/bᵢ + gᴱᵣ/Λ
Λ = 1/(r₂ - r₁) * log((1 - r₂)/(1 - r₁))
```

## モデル構築の例

```
# デフォルトデータベースを使用
mixing = gErRule(["water","carbon dioxide"]) #デフォルト: NRTL活動係数。
mixing = gErRule(["water","carbon dioxide"],activity = Wilson) #別の活動係数モデルを渡す。
mixing = gErRule([("ethane",["CH3" => 2]),("butane",["CH2" => 2,"CH3" => 2])],activity = UNIFAC) #GC活動係数モデルを渡す。

# 事前構築されたモデルを渡す

act_model = NRTL(["water","ethanol"],userlocations = (a = [0.0 3.458; -0.801 0.0],b = [0.0 -586.1; 246.2 0.0], c = [0.0 0.3; 0.3 0.0]))
mixing = gErRule(["water","ethanol"],activity = act_model)

# ユーザー提供のパラメータを使用

# ファイルまたはフォルダを渡す
mixing = gErRule(["water","ethanol"]; activity = NRTL, activity_userlocations = ["path/to/my/db","nrtl_ge.csv"])

# パラメータを直接渡す
mixing = gErRule(["water","ethanol"];
                activity = NRTL,
                userlocations = (a = [0.0 3.458; -0.801 0.0],
                    b = [0.0 -586.1; 246.2 0.0],
                    c = [0.0 0.3; 0.3 0.0])
                )
```

## 参考文献

1. Piña-Martinez, A., Privat, R., Nikolaidis, I. K., Economou, I. G., & Jaubert, J.-N. (2021). What is the optimal activity coefficient model to be combined with the translated–consistent Peng–Robinson equation of state through advanced mixing rules? Cross-comparison and grading of the Wilson, UNIQUAC, and NRTL aE models against a benchmark database involving 200 binary systems. Industrial & Engineering Chemistry Research, 60(47), 17228–17247. [doi:10.1021/acs.iecr.1c03003](https://doi.org/10.1021/acs.iecr.1c03003)
