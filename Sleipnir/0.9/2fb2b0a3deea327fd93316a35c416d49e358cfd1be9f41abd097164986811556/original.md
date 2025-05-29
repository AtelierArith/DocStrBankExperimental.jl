A mutable struct representing a 2D climate for a glacier with various buffers and datasets.

```
Climate2D{F <: AbstractFloat}
```

# Keyword arguments

  * `raw_climate::RasterStack`: Raw climate dataset for the whole simulation.
  * `climate_raw_step::RasterStack`: Raw climate trimmed for the current step to avoid memory allocations.
  * `climate_step::Dict`: Climate data for the current step.
  * `climate_2D_step::Climate2Dstep`: 2D climate data for the current step to feed to the mass balance (MB) model.
  * `longterm_temps::Vector{F}`: Long-term temperatures for the ice rheology.
  * `avg_temps::F`: Intermediate buffer for computing average temperatures.
  * `avg_gradients::F`: Intermediate buffer for computing average gradients.
