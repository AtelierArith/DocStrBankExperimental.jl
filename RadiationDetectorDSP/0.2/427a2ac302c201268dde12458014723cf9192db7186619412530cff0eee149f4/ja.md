simple*csa*response*filter(τ*rise::Real, τ*decay::Real, gain::Real = one(τ*rise))

DSP.jlに互換性のあるフィルターを返し、典型的な電荷感受性増幅器（CSA）の応答をモデル化します。
