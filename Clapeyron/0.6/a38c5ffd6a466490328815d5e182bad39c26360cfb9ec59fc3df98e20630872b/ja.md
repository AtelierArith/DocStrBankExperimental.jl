```
MonomerIdeal <: MonomerIdealModel

MonomerIdeal(components; 
userlocations = String[],
reference_state = nothing,
verbose = false)
```

## 入力パラメータ

  * `Mw`: 単一パラメータ (`Float64`) - 分子量 `[g/mol]`

## モデルパラメータ

なし

## 説明

モノマー理想モデル、統計力学から得られた結果 `Λ`

```
    Λᵢ = h/√(kᵦTMwᵢ/Nₐ)    
    a₀ = A₀/nRT = ∑xᵢlog(ρᵢΛᵢ^3)
```

## モデル構築の例

```
# デフォルトデータベースを使用
idealmodel = MonomerIdeal("water") #単一入力
idealmodel = MonomerIdeal(["water","ethanol"]) #複数成分

# ユーザー提供のパラメータを使用

# ファイルまたはフォルダを渡す
idealmodel = MonomerIdeal(["neon","hydrogen"]; userlocations = ["path/to/my/db","mw.csv"])

# パラメータを直接渡す
idealmodel = MonomerIdeal(["neon","hydrogen"];userlocations = (;Mw = [20.17, 2.]))
```
