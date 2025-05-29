aspure(krs::Union{KRatio, KRatios}, mc::Type{<:MatrixCorrection} = XPP, fc::Type{<:FluorescenceCorrection} = NullFluorescence, cc::Type{<:CoatingCorrection} = NullCoating)

Reinterprete a k-ratio or k-ratios as relative to a pure, uncoated element at the same beam energy and take-off angle as the unknown.
