```
VTPRRule{γ} <: VTPRRuleModel

VTPRRule(components;
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

体積変換ペン-ロビンソン [`VTPR`](@ref) 状態方程式によって使用される混合ルール。過剰残余ギブズエネルギー関数 `Clapeyron.excess_g_res(model,P,T,z)` 関数を定義する活動モデル（[`UNIQUAC`](@ref) および [`UNIFAC`](@ref) モデルなど）でのみ機能します。

```
aᵢⱼ = √(aᵢaⱼ)(1-kᵢⱼ)
bᵢⱼ = ((bᵢ^(3/4) + bⱼ^(3/4))/2)^(4/3)
log(γʳ)ᵢ = lnγ_res(model.activity,V,T,z)
gᴱᵣₑₛ = ∑RTlog(γʳ)ᵢxᵢ
b̄ = ∑bᵢⱼxᵢxⱼ
c̄ = ∑cᵢxᵢ
ā = b̄RT(∑[xᵢaᵢᵢαᵢ/(RTbᵢᵢ)] - gᴱᵣₑₛ/(0.53087RT))
```

## モデル構築の例

```
# 注意: このモデルはVTPRUNIFAC活動モデル専用に使用されることを意図しています。

# デフォルトデータベースを使用
mixing = VTPRRule(["water","carbon dioxide"]) #デフォルト: VTPRUNIFAC 活動係数。
mixing = VTPRRule(["water","carbon dioxide"],activity = NRTL) #別の活動係数モデルを渡す
mixing = VTPRRule([("ethane",["CH3" => 2]),("butane",["CH2" => 2,"CH3" => 2])],activity = UNIFAC) #GC活動係数モデルを渡す。

# 事前構築されたモデルを渡す

act_model = NRTL(["water","ethanol"],userlocations = (a = [0.0 3.458; -0.801 0.0],b = [0.0 -586.1; 246.2 0.0], c = [0.0 0.3; 0.3 0.0]))
mixing = VTPRRule(["water","ethanol"],activity = act_model)

# ユーザー提供のパラメータを使用

# ファイルまたはフォルダを渡す
mixing = VTPRRule(["water","ethanol"]; activity = NRTL, activity_userlocations = ["path/to/my/db","nrtl_ge.csv"])

# パラメータを直接渡す
mixing = VTPRRule(["water","ethanol"];
                activity = NRTL,
                userlocations = (a = [0.0 3.458; -0.801 0.0],
                    b = [0.0 -586.1; 246.2 0.0],
                    c = [0.0 0.3; 0.3 0.0])
                )
```

## 参考文献

1. Ahlers, J., & Gmehling, J. (2001). Development of an universal group contribution equation of state. Fluid Phase Equilibria, 191(1–2), 177–188. [doi:10.1016/s0378-3812(01)00626-4](https://doi.org/10.1016/s0378-3812(01)00626-4)
