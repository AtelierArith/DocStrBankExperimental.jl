```
function evaluate_mps(
    mps::Union{ITensorMPS.MPS,ITensorMPS.MPO},
    indexspecs::Vararg{AbstractVector{<:Tuple{ITensorMPS.Index,Int}}}
)
```

与えられたインデックス値のセットに対してMPSまたはMPOを評価します。

  * `indexspec`はタプルのリストであり、各タプルはインデックスを指定する`ITensorMPS.Index`オブジェクトと、指定されたインデックスの値に対応する`Int`を含みます。

多くの評価が必要な場合は、最初にMPSを`TensorCrossInterpolation.TTCache`オブジェクトに変換することが有利かもしれません。
