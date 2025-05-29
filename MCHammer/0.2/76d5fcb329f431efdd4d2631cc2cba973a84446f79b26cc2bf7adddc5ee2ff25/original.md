Triple exponential smoothing (Holt–Winters) model.

# Fields

  * `season_length::Int`: Number of periods in a season (e.g., 12 for monthly data).
  * `alpha::Float64`: Level smoothing constant.
  * `beta::Float64`: Trend smoothing factor.
  * `gamma::Float64`: Seasonal smoothing factor.
