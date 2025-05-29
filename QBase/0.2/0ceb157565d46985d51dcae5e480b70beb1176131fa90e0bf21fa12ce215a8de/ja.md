```
POVMel( M :: AbstractMatrix{T<:Number}; atol=ATOL :: Float64) <: Operator{T}
```

A [`POVM`](@ref) 要素。行列 `M` がエルミートでなく、絶対許容誤差 `atol` の範囲内で正定値でない場合、`DomainError` がスローされます。
