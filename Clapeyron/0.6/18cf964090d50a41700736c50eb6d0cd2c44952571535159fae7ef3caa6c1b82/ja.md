```
vdW(components;
idealmodel = BasicIdeal,
alpha = NoAlpha,
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

ファン・デル・ワールス状態方程式。

```
P = RT/(V-Nb) + a•α(T)/V²
```

## モデル構築の例

```julia
# デフォルトデータベースを使用
model = vdW("water") #単一入力
model = vdW(["water","ethanol"]) #複数成分
model = vdW(["water","ethanol"], idealmodel = ReidIdeal) #理想モデルの修正
model = vdW(["water","ethanol"],alpha = SoaveAlpha) #アルファ関数の修正
model = vdW(["water","ethanol"],translation = RackettTranslation) #翻訳の修正
model = vdW(["water","ethanol"],mixing = KayRule) #別の混合ルールを使用
model = vdW(["water","ethanol"],mixing = WSRule, activity = NRTL) #高度なEoS+gᴱ混合ルールを使用

# 事前構築されたモデルを渡す

my_alpha = SoaveAlpha(["ethane","butane"],userlocations = Dict(:acentricfactor => [0.1,0.2]))
model = vdW(["ethane","butane"],alpha = my_alpha)

# ユーザー提供のパラメータ、ファイルまたはフォルダを渡す

model = vdW(["neon","hydrogen"]; userlocations = ["path/to/my/db","cubic/my_k_values.csv"])

# ユーザー提供のパラメータ、パラメータを直接渡す

model = vdW(["neon","hydrogen"];
        userlocations = (;Tc = [44.492,33.19],
                        Pc = [2679000, 1296400],
                        Mw = [20.17, 2.],
                        acentricfactor = [-0.03,-0.21]
                        k = [0. 0.18; 0.18 0.], #k,lは単一成分モデルでは省略可能。
                        l = [0. 0.01; 0.01 0.])
                    )
```

## 参考文献

1. van der Waals JD. Over de Continuiteit van den Gasen Vloeistoftoestand. PhD thesis, University of Leiden; 1873
