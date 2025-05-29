simple*csa*response*filter(τ*rise::Real, τ*decay::Real, gain::Real = one(τ*rise))

Return a DSP.jl-compatible filter that models the response of a typical charge-sensitive amplifier (CSA).
