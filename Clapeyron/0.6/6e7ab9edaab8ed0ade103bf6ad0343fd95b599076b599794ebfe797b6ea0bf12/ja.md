```
BasicIdeal <: IdealModel

BasicIdeal(components;
userlocations = String[],
reference_state = nothing,
verbose = false)
```

## 入力パラメータ

なし

## 説明

デフォルトの理想モデル。定数比熱容量は `5R/2` に等しい。ヘルムホルツエネルギーは次のように表される：

```
    a₀ = A₀/nRT = ∑(xᵢlog(nxᵢ/V)) - 1 - 1.5log(T)
```

## モデル構築の例

```
# このモデルにはパラメータがないため、これらのコンストラクタはすべて同等です：
idealmodel = BasicIdeal()
idealmodel = BasicIdeal("water")
idealmodel = BasicIdeal(["water","carbon dioxide"])
```
