radiationDirectionCoeff(md::MagneticDipole{FT}, θϕ::θϕInfo{FT}) where {FT<:Real}

方向性係数を計算します：$D_m(θ, ϕ) = 4π U_m(θ, ϕ)/P_{rad}$。
