```
PSRKRule{γ} <: MHV1RuleModel

PSRKRule(components;
activity = Wilson,
userlocations = String[],
activity_userlocations = String[],
verbose::Bool=false)
```

## 入力パラメータ

なし

## 入力モデル

  * `activity`: 活動モデル

## 説明

予測的ソーヴェ-レドリッヒ-クウォン [`PSRK`](@ref) EoS によって使用される混合ルールで、第一種修正ヒューロン-ビダル混合ルールから導出されています。

## モデル構築の例

```
# 注意: このモデルはPSRKUNIFAC活動モデルと専ら使用されることを意図しています。

# デフォルトデータベースを使用
mixing = PSRKRule(["water","carbon dioxide"]) #デフォルト: PSRKUNIFAC 活動係数。
mixing = PSRKRule(["water","carbon dioxide"],activity = NRTL) #別の活動係数モデルを渡す
mixing = PSRKRule([("ethane",["CH3" => 2]),("butane",["CH2" => 2,"CH3" => 2])],activity = UNIFAC) #GC活動係数モデルを渡す。

# 事前構築されたモデルを渡す

act_model = NRTL(["water","ethanol"],userlocations = (a = [0.0 3.458; -0.801 0.0],b = [0.0 -586.1; 246.2 0.0], c = [0.0 0.3; 0.3 0.0]))
mixing = PSRKRule(["water","ethanol"],activity = act_model)

# ユーザー提供のパラメータを使用

# ファイルまたはフォルダを渡す
mixing = PSRKRule(["water","ethanol"]; activity = NRTL, activity_userlocations = ["path/to/my/db","nrtl_ge.csv"])

# パラメータを直接渡す
mixing = PSRKRule(["water","ethanol"];
                activity = NRTL,
                userlocations = (a = [0.0 3.458; -0.801 0.0],
                    b = [0.0 -586.1; 246.2 0.0],
                    c = [0.0 0.3; 0.3 0.0])
                )
```
