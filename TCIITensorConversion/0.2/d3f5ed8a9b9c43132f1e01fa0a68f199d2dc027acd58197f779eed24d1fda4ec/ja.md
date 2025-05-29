```
function evaluate_mps(
    mps::Union{ITensorMPS.MPS,ITensorMPS.MPO},
    indices::AbstractVector{<:ITensorMPS.Index},
    indexvalues::AbstractVector{Int}
)
```

与えられたインデックス値のセットに対してMPSまたはMPOを評価します。

  * `indices`は、インデックスが与えられる順序を指定する`ITensorMPS.Index`オブジェクトのリストです。
  * `indexvalues`は、`indices`と同じ順序の整数値のリストです。

多くの評価が必要な場合は、最初にMPSを`TensorCrossInterpolation.TTCache`オブジェクトに変換することが有利かもしれません。
