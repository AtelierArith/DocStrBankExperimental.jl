SubspaceOp(basis::AbstractMatrix{T},shape::NTuple{D,Int64},numContr) where {T,D}

basisは特定のレベルに切り取られたsvd_object.Vに対応します

basisの型はrawdataの型に対応する必要があります
