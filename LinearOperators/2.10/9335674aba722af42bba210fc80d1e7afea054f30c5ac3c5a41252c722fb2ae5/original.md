LinearOperator(M::Symmetric{T}, S = Vector{T}) where {T <: Real} =

Construct a linear operator from a symmetric real square matrix `M`. Change `S` to use LinearOperators on GPU.
