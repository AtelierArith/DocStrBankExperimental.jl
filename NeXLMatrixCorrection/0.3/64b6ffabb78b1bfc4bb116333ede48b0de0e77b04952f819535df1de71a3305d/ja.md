aspure(krs::Union{KRatio, KRatios}, mc::Type{<:MatrixCorrection} = XPP, fc::Type{<:FluorescenceCorrection} = NullFluorescence, cc::Type{<:CoatingCorrection} = NullCoating)

未知数と同じビームエネルギーおよび取り出し角度で純粋な無被覆元素に対してk比またはk比を再解釈します。
