```
AcbVector <: DenseVector{Acb}
AcbVector(n::Integer; prec::Integer = _current_precision())
AcbVector(v::AcbVectorLike; shallow::Bool = false, prec::Integer = precision(v))
AcbVector(v::AbstractVector; prec::Integer = _precision(v))

`n::Integer`を持つコンストラクタは、ゼロで埋められた`n`要素のベクトルを返します。他の2つのコンストラクタは、与えられたベクトルのコピーを返します。`shallow = true`の場合、返されたベクトルは入力と基盤データを共有し、一方を変更すると両方が変更されます。

詳細は[`AcbRefVector`](@ref)を参照してください。
```
