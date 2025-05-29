"     massthickness(ty::Type{<:MatrixCorrection}, subtrate::Material, coating::Material, cxr::CharXRay, e0::AbstractFloat, toa::AbstractFloat, k::AbstractFloat)

`coating`材料の超薄層の質量厚さを、特性X線`cxr`の測定されたk比`k`から`substrate`上で推定します。k比が1%のオーダーで機能します。コーティングの標準は、コーティングと同じ材料であると仮定されています。
