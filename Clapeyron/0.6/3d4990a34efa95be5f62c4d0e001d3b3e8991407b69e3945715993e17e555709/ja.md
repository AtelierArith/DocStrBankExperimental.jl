```
MHV2Rule{γ} <: MHV2RuleModel

MHV2Rule(components;
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

修正ヒューロン-ビダル混合則、第二次。

```
bᵢⱼ = (1 - lᵢⱼ)(bᵢ + bⱼ)/2
b̄ = ∑bᵢⱼxᵢxⱼ
c̄ = ∑cᵢxᵢ
ᾱᵢ  = aᵢαᵢ/bᵢRT
ċ = -q₁*Σᾱᵢxᵢ - q₂*Σᾱᵢxᵢ^2 - gᴱ/RT - ∑log(bᵢᵢ/b̄)
ā = (-q₁ - √(q₁^2 - 4q₂ċ))/(2q₂)

モデルがペン-ロビンソンの場合：
    q₁ = -0.4347, q₂ = -0.003654
モデルがレドリッヒ-クウォングの場合：
    q₁ = -0.4783, q₂ = -0.0047
    (-0.4783,-0.0047)
```

`q₁` と `q₂` に異なる値を使用するには、`Clapeyron.MHV1q(::CubicModel,::MHV2Model) = (q₁,q₂)` をオーバーロードします。

## モデル構築の例

```
# デフォルトデータベースを使用
mixing = MHV2Rule(["water","carbon dioxide"]) #デフォルト: ウィルソン活動係数。
mixing = MHV2Rule(["water","carbon dioxide"],activity = NRTL) #別の活動係数モデルを渡す。
mixing = MHV2Rule([("ethane",["CH3" => 2]),("butane",["CH2" => 2,"CH3" => 2])],activity = UNIFAC) #GC活動係数モデルを渡す。

# 事前構築されたモデルを渡す

act_model = NRTL(["water","ethanol"],userlocations = (a = [0.0 3.458; -0.801 0.0],b = [0.0 -586.1; 246.2 0.0], c = [0.0 0.3; 0.3 0.0]))
mixing = MHV2Rule(["water","ethanol"],activity = act_model)

# ユーザー提供のパラメータを使用

# ファイルまたはフォルダを渡す
mixing = MHV2Rule(["water","ethanol"]; activity = NRTL, activity_userlocations = ["path/to/my/db","nrtl_ge.csv"])

# パラメータを直接渡す
mixing = MHV1Rule(["water","ethanol"];
                activity = NRTL,
                userlocations = (a = [0.0 3.458; -0.801 0.0],
                    b = [0.0 -586.1; 246.2 0.0],
                    c = [0.0 0.3; 0.3 0.0])
                )
```

## 参考文献

1. Michelsen, M. L. (1990). A modified Huron-Vidal mixing rule for cubic equations of state. Fluid Phase Equilibria, 60(1–2), 213–219. [doi:10.1016/0378-3812(90)85053-d](https://doi.org/10.1016/0378-3812(90)85053-d)
