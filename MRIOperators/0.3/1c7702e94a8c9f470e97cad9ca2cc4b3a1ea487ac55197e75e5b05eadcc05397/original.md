SubspaceOp(basis::AbstractMatrix{T},shape::NTuple{D,Int64},numContr) where {T,D}

basis correspond to svd_object.V cropped to a certain level

basis type should correspond to the type of the rawdata
