SeisHypEvents(; <keyword arguments>)

Generate two dimensional data consisting of hyperbolic events.

# Arguments

  * `ot::Real=0.0`: first sample for the time axis in secs.
  * `dt::Real=0.004`: time sampling interval in secs.
  * `nt::Int=301`: number of time samples.
  * `ox::Real=-1000.0`: first sample for spatial dimension in meters.
  * `dx::Real=20.0`: sample interval for the spatial dimension in meters.
  * `nx::Int=101`: number of samples for the spatial dimension.
  * `tau::Vector{Real}=[0.2, 0.6, 0.9]`: intercept traveltimes for each event.
  * `vel::Vector{Real}=[1500.0, 2000.0, 3000.0]`: rms velocities in m/s
  * `apex::Vector{Real}=[0.0, 0.0, 0.0]`: apex-shifts in meters.
  * `amp::Vector{Real}=[1.0, -1.0, 1.0]`: amplitudes for each event.
  * `wavelet::AbstractString="ricker"`: wavelet used to model the events.
  * `f0::Vector{Real}=[20.0]`: central frequency of wavelet for each event.

# Output

  * `d::Array{Real, 2}`: two dimensional data consisting of hyperbolic events.

# Examples

```julia
julia> using SeisPlot
julia> d = SeisHypEvents(); SeisPlotTX(d);
julia> d = SeisHypEvents(apex=[100, 200, -300], f0=[30, 20, 15]);
SeisPlotTX(d);
```
