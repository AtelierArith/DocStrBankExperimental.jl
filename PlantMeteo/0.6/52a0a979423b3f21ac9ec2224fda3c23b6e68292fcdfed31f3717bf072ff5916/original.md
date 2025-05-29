```
to_daily(df, args...)
to_daily(t::T, args...) where {T<:TimeStepTable{<:Atmosphere}}
```

Transform a `DataFrame` object or `TimeStepTable{<:Atmosphere}` with sub-daily time steps (*e.g.* 1h) to a daily time-step table.

# Arguments

  * `t`: a `TimeStepTable{<:Atmosphere}` with sub-daily time steps (*e.g.* 1h)
  * `args`: a list of transformations to apply to the data, formates as for `DataFrames.jl`

# Notes

Default transformations are applied to the data, and can be overriden by the user. The default transformations are:

  * `:date => (x -> unique(Dates.Date.(x))) => :date`: the date is transformed into a `Date` object
  * `:duration => sum => :duration`: the duration is summed
  * `:T => minimum => :Tmin`: we use the minimum temperature for Tmin
  * `:T => maximum => :Tmax`: and the maximum temperature for Tmax
  * `:Precipitations => sum => :Precipitations`: the precipitations are summed
  * `:Rh => mean => :Rh`: the relative humidity is averaged
  * `:Wind, :P, :Rh, :Cₐ, :e, :eₛ, :VPD, :ρ, :λ, :γ, :ε, :Δ, :clearness` are

all averaged

  * `[:Ri_SW_f, :duration] => ((x, y) -> sum(x .* Dates.toms.(y)) * 1.0e-9) => :Ri_SW_f`: the irradiance is integrated, so its unit chaneges from W m⁻² to MJ m⁻² d⁻¹
  * All other irradiance variables are also integrated (see the code for details)

Note that the default transformations can be overriden by the user, and that the default transformations are only applied if the variable is available.

# Examples

```julia
using PlantMeteo, Dates
# Forecast for today and tomorrow:
period = [today(), today()+Dates.Day(1)]
w = get_weather(48.8566, 2.3522, period)
# Convert to daily:
w_daily = to_daily(w, :T => mean => :Tmean)
```
