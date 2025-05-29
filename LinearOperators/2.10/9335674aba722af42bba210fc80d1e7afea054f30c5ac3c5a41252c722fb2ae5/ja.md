LinearOperator(M::Symmetric{T}, S = Vector{T}) where {T <: Real} =

対称実正方行列 `M` から線形演算子を構築します。`S` を使用してGPU上のLinearOperatorsに変更します。
