```
NaNLiquid <: IdealModel

NaNLiquid(components; 
userlocations = String[],
reference_state = nothing,
verbose = false)
```

## 入力パラメータ

なし

## 説明

プレースホルダー液体モデル。任意の入力に対してNaNを返します。

## モデル構築の例

```
# このモデルにはパラメータがないため、これらのコンストラクタはすべて同等です：
liquid = NaNLiquid()
liquid = NaNLiquid("water")
liquid = NaNLiquid(["water","carbon dioxide"])
```
