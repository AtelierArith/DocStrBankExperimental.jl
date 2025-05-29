```
MHV1Rule{γ} <: MHV1RuleModel

MHV1Rule(components;
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

修正ヒューロン-ビダル混合則、一次

```
bᵢⱼ = (1 - lᵢⱼ)(bᵢ + bⱼ)/2
b̄ = ∑bᵢⱼxᵢxⱼ
c̄ = ∑cᵢxᵢ
ā = b̄RT(∑[xᵢaᵢᵢαᵢ/(RTbᵢᵢ)] - [gᴱ/RT + ∑log(bᵢᵢ/b̄)]/q)

モデルがペン-ロビンソンの場合:
    q = 0.53
モデルがレドリッヒ-クウォンの場合:
    q = 0.593
```

異なる値の `q` を使用するには、`Clapeyron.MHV1q(::CubicModel,::MHV1Model) = q` をオーバーロードします。

## モデル構築の例

```
# デフォルトデータベースを使用
mixing = MHV1Rule(["water","carbon dioxide"]) #デフォルト: ウィルソンアクティビティ係数。
mixing = MHV1Rule(["water","carbon dioxide"],activity = NRTL) #別のアクティビティ係数モデルを渡す。
mixing = MHV1Rule([("ethane",["CH3" => 2]),("butane",["CH2" => 2,"CH3" => 2])],activity = UNIFAC) #GCアクティビティ係数モデルを渡す。

# 事前構築されたモデルを渡す

act_model = NRTL(["water","ethanol"],userlocations = (a = [0.0 3.458; -0.801 0.0],b = [0.0 -586.1; 246.2 0.0], c = [0.0 0.3; 0.3 0.0]))
mixing = MHV1Rule(["water","ethanol"],activity = act_model)

# ユーザー提供のパラメータを使用

# ファイルまたはフォルダを渡す
mixing = MHV1Rule(["water","ethanol"]; activity = NRTL, activity_userlocations = ["path/to/my/db","nrtl_ge.csv"])

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
