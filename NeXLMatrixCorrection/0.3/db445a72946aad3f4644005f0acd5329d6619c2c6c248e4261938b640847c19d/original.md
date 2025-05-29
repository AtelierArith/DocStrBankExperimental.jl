"     massthickness(ty::Type{<:MatrixCorrection}, subtrate::Material, coating::Material, cxr::CharXRay, e0::AbstractFloat, toa::AbstractFloat, k::AbstractFloat)

Estimate the mass-thickness of a ultra-thin layer of a `coating` material on a `substrate` from a measured k-ratio `k` of a characteristic X-ray `cxr`.  Works for k-ratios of the order of 1 %.  The standard for the coating is assumed to be of the same material as the coating.
