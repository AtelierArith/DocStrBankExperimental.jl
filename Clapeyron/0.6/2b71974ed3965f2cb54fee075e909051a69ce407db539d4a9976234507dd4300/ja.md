```
HVRule{γ} <: HVRuleModel

HVRule(components;
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

Huron-Vidal混合則

```
b̄ = ∑bᵢⱼxᵢxⱼ
c̄ = ∑cᵢxᵢ
ā = b̄(∑[xᵢaᵢᵢαᵢ/(bᵢᵢ)] - gᴱ/λ)
for Redlich-Kwong:
    λ = log(2) (0.6931471805599453)
for Peng-Robinson:
    λ = 1/(2√(2))log((2+√(2))/(2-√(2))) (0.6232252401402305)
```

`λ`は、無限圧力下での`gᴱ`と`gᴱ(cubic)`の関係を示す係数です。詳細については[1]を参照してください。`HV_λ(::HVRuleModel,::CubicModel,z)`を定義することでカスタマイズできます。

## 参考文献

1. Huron, M.-J., & Vidal, J. (1979). New mixing rules in simple equations of state for representing vapour-liquid equilibria of strongly non-ideal mixtures. Fluid Phase Equilibria, 3(4), 255–271. [doi:10.1016/0378-3812(79)80001-1](https://doi.org/10.1016/0378-3812(79)80001-1)

## モデル構築の例

```
# デフォルトデータベースを使用
mixing = HVRule(["water","carbon dioxide"]) #デフォルト: Wilson活動係数。
mixing = HVRule(["water","carbon dioxide"],activity = NRTL) #別の活動係数モデルを渡す。
mixing = HVRule([("ethane",["CH3" => 2]),("butane",["CH2" => 2,"CH3" => 2])],activity = UNIFAC) #GC活動係数モデルを渡す。

# 事前構築されたモデルを渡す

act_model = NRTL(["water","ethanol"],userlocations = (a = [0.0 3.458; -0.801 0.0],b = [0.0 -586.1; 246.2 0.0], c = [0.0 0.3; 0.3 0.0]))
mixing = HVRule(["water","ethanol"],activity = act_model)

# ユーザー提供のパラメータを使用

# ファイルまたはフォルダを渡す
mixing = HVRule(["water","ethanol"]; activity = NRTL, activity_userlocations = ["path/to/my/db","nrtl_ge.csv"])

# パラメータを直接渡す
mixing = HVRule(["water","ethanol"];
                activity = NRTL,
                userlocations = (a = [0.0 3.458; -0.801 0.0],
                    b = [0.0 -586.1; 246.2 0.0],
                    c = [0.0 0.3; 0.3 0.0])
                )
```
