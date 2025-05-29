```
PR78(components::Vector{String};
idealmodel = BasicIdeal,
alpha = PR78Alpha,
mixing = vdW1fRule,
activity = nothing,
translation = NoTranslation,
userlocations = String[], 
ideal_userlocations = String[],
alpha_userlocations = String[],
mixing_userlocations = String[],
translation_userlocations = String[],
reference_state = nothing,
verbose = false)
```

ペン・ロビンソン（1978）状態方程式。以下のモデルを使用します：

  * 翻訳モデル: [`NoTranslation`](@ref)
  * アルファモデル: [`PR78Alpha`](@ref)
  * 混合則モデル: [`vdW1fRule`](@ref)

## モデル構築の例

```julia
# デフォルトデータベースを使用
model = PR78("water") #単一入力
model = PR78(["water","ethanol"]) #複数成分
model = PR78(["water","ethanol"], idealmodel = ReidIdeal) #理想モデルの修正
model = PR78(["water","ethanol"],alpha = Soave2019) #アルファ関数の修正
model = PR78(["water","ethanol"],translation = RackettTranslation) #翻訳の修正
model = PR78(["water","ethanol"],mixing = KayRule) #別の混合則の使用
model = PR78(["water","ethanol"],mixing = WSRule, activity = NRTL) #高度なEoS+gᴱ混合則の使用

# 事前構築されたモデルを渡す

my_alpha = PRAlpha(["ethane","butane"],userlocations = Dict(:acentricfactor => [0.1,0.2]))
model = PR78(["ethane","butane"],alpha = my_alpha) #このモデルは通常のPR EoSになります

# ユーザー提供のパラメータ、ファイルまたはフォルダを渡す
model = PR78(["neon","hydrogen"]; userlocations = ["path/to/my/db","cubic/my_k_values.csv"])

# ユーザー提供のパラメータ、パラメータを直接渡す

model = PR78(["neon","hydrogen"];
        userlocations = (;Tc = [44.492,33.19],
                        Pc = [2679000, 1296400],
                        Mw = [20.17, 2.],
                        acentricfactor = [-0.03,-0.21]
                        k = [0. 0.18; 0.18 0.], #k,lは単一成分モデルでは省略可能です。
                        l = [0. 0.01; 0.01 0.])
                    )
```

## 参考文献

1. Robinson DB, Peng DY. The characterization of the heptanes and heavier fractions for the GPA Peng-Robinson programs. Tulsa: Gas Processors Association; 1978
