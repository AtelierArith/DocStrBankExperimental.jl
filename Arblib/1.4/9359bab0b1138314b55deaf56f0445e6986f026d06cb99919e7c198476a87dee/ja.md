```
ArbVector <: DenseVector{Arb}
ArbVector(n::Integer; prec::Integer = _current_precision())
ArbVector(v::ArbVectorLike; shallow::Bool = false, prec::Integer = precision(v))
ArbVector(v::AbstractVector; prec::Integer = _precision(v))
```

`n::Integer`を持つコンストラクタは、ゼロで埋められた`n`要素のベクトルを返します。他の2つのコンストラクタは、与えられたベクトルのコピーを返します。`shallow = true`の場合、返されたベクトルは入力と基盤データを共有し、一方を変更すると両方が変更されます。

詳細は[`ArbRefVector`](@ref)を参照してください。
