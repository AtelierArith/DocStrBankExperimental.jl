```
AcbMatrix <: DenseMatrix{Acb}
AcbMatrix(r::Integer, c::Integer; prec::Integer = _current_precision())
AcbMatrix(A::AcbMatrixLike; shallow::Bool = false, prec::Integer = precision(v))
AcbMatrix(A::AbstractMatrix; prec::Integer = _precision(v))
AcbMatrix(v::AbstractVector; prec::Integer = _precision(v))
```

`r::Integer, c::Integer`を持つコンストラクタは、ゼロで埋められた`r × c`を返します。他の3つのコンストラクタは、与えられた行列またはベクトルのコピーを返します。`shallow = true`の場合、返された行列は入力と基盤データを共有し、一方を変更すると両方が変更されます。

[`AcbRefMatrix`](@ref)も参照してください。
