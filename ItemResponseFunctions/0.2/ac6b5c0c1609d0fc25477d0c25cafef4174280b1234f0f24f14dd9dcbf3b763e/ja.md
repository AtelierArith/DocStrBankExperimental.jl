```julia
struct ItemParameters{M<:AbstractItemResponseModels.ItemResponseModel, N, T<:Real}
```

アイテム応答モデルのためのアイテムパラメータを表す構造体。

## フィールド

  * `a`: アイテムの識別力
  * `b`: アイテムの難易度（位置）
  * `c`: 下限漸近線
  * `d`: 上限漸近線
  * `e`: アイテムの剛性
  * `t`: 閾値パラメータのタプル

## 例

```jldoctest
julia> pars = ItemParameters(TwoPL, a = 1.5, b = 0.0)
ItemParameters{TwoParameterLogisticModel, 0, Float64}(1.5, 0.0, 0.0, 1.0, 1.0, ())

julia> ItemParameters(OnePL, pars)
ItemParameters{OneParameterLogisticModel, 0, Float64}(1.0, 0.0, 0.0, 1.0, 1.0, ())
```
