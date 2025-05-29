```
ShomateIdeal <: ShomateIdealModel

ShomateIdeal(components; 
userlocations = String[],
reference_state = nothing,
verbose = false)
```

## 入力パラメータ

  * `a`: 単一パラメータ (`Float64`) - 多項式係数
  * `b`: 単一パラメータ (`Float64`) - 多項式係数
  * `c`: 単一パラメータ (`Float64`) - 多項式係数
  * `d`: 単一パラメータ (`Float64`) - 多項式係数
  * `e`: 単一パラメータ（オプション） (`Float64`)  - 1/T^2 の多項式係数
  * `Mw`: 単一パラメータ (`Float64`)（オプション） - 分子量 `[g/mol]`

## モデルパラメータ

  * `a`: 単一パラメータ (`Float64`) - 多項式係数
  * `b`: 単一パラメータ (`Float64`) - 多項式係数
  * `c`: 単一パラメータ (`Float64`) - 多項式係数
  * `d`: 単一パラメータ (`Float64`) - 多項式係数
  * `e`: 単一パラメータ（オプション） (`Float64`)  - 1/T^2 の多項式係数
  * `coeffs`: 単一パラメータ (`NTuple{5,Float64}`)
  * `Mw`: 単一パラメータ (`Float64`)（オプション） - 分子量 `[g/mol]`

## 説明

Shomate理想モデル。特定熱容量の積分によって得られるヘルムホルツエネルギー：

```
Cpᵢ(T) = aᵢ  + bᵢT + cᵢT^2 + dᵢT^3 + eᵢT^-2
Cp(T) = ∑Cpᵢxᵢ
```

## モデル構築の例

```
# デフォルトデータベースを使用
idealmodel = ShomateIdeal("water") #単一入力
idealmodel = ShomateIdeal(["water","ethanol"]) #複数成分

# ユーザー提供のパラメータを使用

# ファイルまたはフォルダを渡す
idealmodel = ShomateIdeal(["neon","hydrogen"]; userlocations = ["path/to/my/db","shomate.csv"])

# パラメータを直接渡す
idealmodel = ShomateIdeal(["water","butane"];
            userlocations = (a = [32.24, 9.487], 
                        b = [0.00192, 0.3313], 
                        c = [1.06e-5, -0.0001108],
                        d = [-3.6e-9, -2.822e-9],
                        Mw = [18.01, 58.12])
                        ) #eは使用されません
```
