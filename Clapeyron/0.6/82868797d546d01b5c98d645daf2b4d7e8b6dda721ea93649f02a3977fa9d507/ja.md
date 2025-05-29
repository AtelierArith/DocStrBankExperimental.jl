```
WSRule{γ} <: WSRuleModel

WSRule(components;
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

Wong-Sandler混合則。

```
aᵢⱼ = √(aᵢaⱼ)(1 - kᵢⱼ)
bᵢⱼ = (bᵢ + bⱼ)/2
c̄ = ∑cᵢxᵢ
B̄ = ΣxᵢxⱼB̄ᵢⱼ
B̄ᵢⱼ = (1 - kᵢⱼ)((bᵢ - aᵢ/RT) + (bⱼ - aⱼ/RT))/2
b̄  = B̄/(1 - gᴱ/λRT - Σxᵢaᵢαᵢ/bᵢRT)
ā = RT(b̄ - B̄)
for Redlich-Kwong:
    λ = log(2) (0.6931471805599453)
for Peng-Robinson:
    λ = 1/(2√(2))log((2+√(2))/(2-√(2))) (0.6232252401402305)
```

`λ`は、無限圧力における`gᴱ`と`gᴱ(cubic)`の関係を示す係数です。詳細については[1]を参照してください。`WS_λ(::WSRuleModel,::CubicModel)`を定義することでカスタマイズできます。

## モデル構築の例

```
# デフォルトデータベースを使用
mixing = WSRule(["water","carbon dioxide"]) #デフォルト: Wilsonアクティビティ係数。
mixing = WSRule(["water","carbon dioxide"],activity = NRTL) #別のアクティビティ係数モデルを渡す。
mixing = WSRule([("ethane",["CH3" => 2]),("butane",["CH2" => 2,"CH3" => 2])],activity = UNIFAC) #GCアクティビティ係数モデルを渡す。

# 事前構築されたモデルを渡す

act_model = NRTL(["water","ethanol"],userlocations = (a = [0.0 3.458; -0.801 0.0],b = [0.0 -586.1; 246.2 0.0], c = [0.0 0.3; 0.3 0.0]))
mixing = WSRule(["water","ethanol"],activity = act_model)

# ユーザー提供のパラメータを使用

# ファイルまたはフォルダを渡す
mixing = WSRule(["water","ethanol"]; activity = NRTL, activity_userlocations = ["path/to/my/db","nrtl_ge.csv"])

# パラメータを直接渡す
mixing = WSRule(["water","ethanol"];
                activity = NRTL,
                userlocations = (a = [0.0 3.458; -0.801 0.0],
                    b = [0.0 -586.1; 246.2 0.0],
                    c = [0.0 0.3; 0.3 0.0])
                )
```

## 参考文献

1. Wong, D. S. H., & Sandler, S. I. (1992). A theoretically correct mixing rule for cubic equations of state. AIChE journal. American Institute of Chemical Engineers, 38(5), 671–680. [doi:10.1002/aic.690380505](https://doi.org/10.1002/aic.690380505)
