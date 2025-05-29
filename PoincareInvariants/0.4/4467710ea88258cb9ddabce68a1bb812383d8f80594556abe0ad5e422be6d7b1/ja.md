```
compute!(pinv::AbstractPoincareInvariant, points::AbstractVector{<:AbstractVector},
    times::Union{AbstractVector{<:Real}, Real}=NaN, p=nothing)
```

は、セットアップオブジェクト `pinv` を使用して、`points` で与えられた軌道のセットに対して各時刻でポアンカレ不変量を計算します。

`points` は軌道の AbstractVector を表します。`points` の各要素は軌道であり、それ自体が何らかの反復可能なものまたはベクトルの `AbstractVector` です。`times` は、`NaN` のような定数であるか、軌道が評価された時刻のベクトルであり、すなわち各軌道の i 番目の位相空間位置が時刻 `times[i]` で評価されたことを意味します。`p` は微分形式に渡される任意のオプションパラメータであり、時間のようなものです。
