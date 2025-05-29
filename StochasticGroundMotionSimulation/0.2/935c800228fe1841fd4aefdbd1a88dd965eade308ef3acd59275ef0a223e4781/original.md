```
peak_factor(m::S, r_ps::T, fas::FourierParameters, sdof::Oscillator, rvt::RandomVibrationParameters; glxi::Vector{Float64}=xn31i, glwi::Vector{Float64}=wn31i, nodes::Int=length(glxi)) where {S<:Real,T<:Real}
```

Peak factor $u_{max} / u_{rms}$ with a switch of `pf_method` to determine the approach adopted. `rvt.pf_method` can currently be one of: 	- `:CL56` for Cartright Longuet-Higgins (1956) 	- `:DK80` for Der Kiureghian (1980), building on Vanmarcke (1975)

Defaults to `:DK80`.
