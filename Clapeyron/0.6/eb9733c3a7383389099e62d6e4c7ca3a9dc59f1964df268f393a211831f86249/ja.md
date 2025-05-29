```
SRK(components::Vector{String};
idealmodel = BasicIdeal,
alpha = SoaveAlpha,
mixing = vdW1fRule,
activity = nothing,
translation = NoTranslation,
userlocations = String[], 
ideal_userlocations = String[],
alpha_userlocations = String[],
mixing_userlocations = String[],
activity_userlocations = String[],
translation_userlocations = String[],
reference_state = nothing,
verbose = false)
```

## 説明

ソアベ-レドリッヒ-クワン方程式。以下のモデルを使用します：

  * 翻訳モデル: [`NoTranslation`](@ref)
  * アルファモデル: [`SoaveAlpha`](@ref)
  * 混合則モデル: [`vdW1fRule`](@ref)

## モデル構築の例

```julia
# デフォルトデータベースを使用
model = SRK("water") #単一入力
model = SRK(["water","ethanol"]) #複数成分
model = SRK(["water","ethanol"], idealmodel = ReidIdeal) #理想モデルの変更
model = SRK(["water","ethanol"],alpha = Soave2019) #アルファ関数の変更、2019年の相関を使用
model = SRK(["water","ethanol"],translation = RackettTranslation) #翻訳の変更
model = SRK(["water","ethanol"],mixing = KayRule) #別の混合則を使用
model = SRK(["water","ethanol"],mixing = WSRule, activity = NRTL) #高度なEoS+gᴱ混合則を使用

# 事前構築されたモデルを渡す

my_alpha = SoaveAlpha(["ethane","butane"],userlocations = Dict(:acentricfactor => [0.1,0.2]))
model = SRK(["ethane","butane"],alpha = my_alpha)

# ユーザー提供のパラメータ、ファイルまたはフォルダを渡す

model = SRK(["neon","hydrogen"]; userlocations = ["path/to/my/db","cubic/my_k_values.csv"])

# ユーザー提供のパラメータ、パラメータを直接渡す

model = SRK(["neon","hydrogen"];
        userlocations = (;Tc = [44.492,33.19],
                        Pc = [2679000, 1296400],
                        Mw = [20.17, 2.],
                        acentricfactor = [-0.03,-0.21]
                        k = [0. 0.18; 0.18 0.], #k,lは単一成分モデルでは省略可能です。
                        l = [0. 0.01; 0.01 0.])
                    )
```

## 参考文献

1. Soave, G. (1972). 修正されたレドリッヒ-クワン方程式からの平衡定数。化学工学科学, 27(6), 1197–1203. [doi:10.1016/0009-2509(72)80096-4](https://doi.org/10.1016/0009-2509(72)80096-4)
