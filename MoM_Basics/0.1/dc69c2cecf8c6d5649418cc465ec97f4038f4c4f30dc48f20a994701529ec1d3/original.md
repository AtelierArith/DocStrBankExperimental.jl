radiationDirectionCoeff(md::MagneticDipole{FT}, θϕ::θϕInfo{FT}) where {FT<:Real}

计算方向性系数：$D_m(θ, ϕ) = 4π U_m(θ, ϕ)/P_{rad}$。
