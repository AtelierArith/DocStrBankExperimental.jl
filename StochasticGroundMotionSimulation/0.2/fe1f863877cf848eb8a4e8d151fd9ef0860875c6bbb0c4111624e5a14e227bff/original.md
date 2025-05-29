excitation*duration(m, r*ps::U, src::SourceParameters{S,T}, rvt::RandomVibrationParameters) where {S<:Float64,T<:Real,U<:Real}

Generic function implementing excitation duration models.

Currently, only the general Boore & Thompson (2014, 2015) models are implemented along with some project-specific models from Edwards (2023) (for South Africa),  and two UK duration models.  The first two are both represented within the Boore & Thompson (2015) paper, so just switch path duration based upon `rvt.dur_region` To activate the Edwards model, use `rvt.dur_ex == :BE23` For the UK models use `rvt.dur_ex == :UKfree` or `rvt.dur_ex == :UKfixed`
