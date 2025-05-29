```
RK(components; 
idealmodel = BasicIdeal,
alpha = PRAlpha,
mixing = vdW1fRule,
activity = nothing,
translation = NoTranslation,
userlocations = String[],
ideal_userlocations = String[],
alpha_userlocations = String[],
mixing_userlocations = String[],
activity_userlocations = String[],
translation_userlocations = String[],
verbose = false,
reference_state = nothing)
```

## 入力パラメータ

  * `Tc`: 単一パラメータ (`Float64`) - 臨界温度 `[K]`
  * `Pc`: 単一パラメータ (`Float64`) - 臨界圧力 `[Pa]`
  * `Mw`: 単一パラメータ (`Float64`) - 分子量 `[g/mol]`
  * `k`: ペアパラメータ (`Float64`) (オプション)
  * `l`: ペアパラメータ (`Float64`) (オプション)

## モデルパラメータ

  * `Tc`: 単一パラメータ (`Float64`) - 臨界温度 `[K]`
  * `Pc`: 単一パラメータ (`Float64`) - 臨界圧力 `[Pa]`
  * `Mw`: 単一パラメータ (`Float64`) - 分子量 `[g/mol]`
  * `a`: ペアパラメータ (`Float64`)
  * `b`: ペアパラメータ (`Float64`)

## 入力モデル

  * `idealmodel`: 理想モデル
  * `alpha`: アルファモデル
  * `mixing`: 混合モデル
  * `activity`: 混合モデルの作成に使用されるアクティビティモデル。
  * `translation`: 翻訳モデル

## 説明

レドリッヒ-クワンゴン状態方程式。

```
P = RT/(V-Nb) + a•α(T)/(V(V+Nb))
```

## モデル構築の例

```julia
# デフォルトデータベースを使用
model = RK("water") #単一入力
model = RK(["water","ethanol"]) #複数成分
model = RK(["water","ethanol"], idealmodel = ReidIdeal) #理想モデルの修正
model = RK(["water","ethanol"],alpha = Soave2019) #アルファ関数の修正
model = RK(["water","ethanol"],translation = RackettTranslation) #翻訳の修正
model = RK(["water","ethanol"],mixing = KayRule) #別の混合ルールを使用
model = RK(["water","ethanol"],mixing = WSRule, activity = NRTL) #高度なEoS+gᴱ混合ルールを使用

# 事前構築されたモデルを渡す

my_alpha = SoaveAlpha(["ethane","butane"],userlocations = Dict(:acentricfactor => [0.1,0.2]))
model = RK(["ethane","butane"],alpha = my_alpha) #これは実質的にSRKモデルです

# ユーザー提供のパラメータ、ファイルまたはフォルダを渡す

# ファイルまたはフォルダを渡す
model = RK(["neon","hydrogen"]; userlocations = ["path/to/my/db","cubic/my_k_values.csv"])

# ユーザー提供のパラメータ、パラメータを直接渡す

model = RK(["neon","hydrogen"];
        userlocations = (;Tc = [44.492,33.19],
                        Pc = [2679000, 1296400],
                        Mw = [20.17, 2.],
                        acentricfactor = [-0.03,-0.21]
                        k = [0. 0.18; 0.18 0.], #k,lは単一成分モデルでは省略可能です。
                        l = [0. 0.01; 0.01 0.])
                    )
```

## 参考文献

1. Redlich, O., & Kwong, J. N. S. (1949). On the thermodynamics of solutions; an equation of state; fugacities of gaseous solutions. Chemical Reviews, 44(1), 233–244. [doi:10.1021/cr60137a013](https://doi.org/10.1021/cr60137a013)
