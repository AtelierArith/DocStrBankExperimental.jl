```
SeisParabEvents(; <keyword arguments>)
```

Generate up to five dimensional data consisting of parabolic events.

# Arguments

  * `ot=0.0`: first sample for the time axis in secs.
  * `dt=0.004`: time sampling interval in secs.
  * `nt=500`: number of time samples.
  * `ox1=0.0`: first sample for the first spatial dimension in meters.
  * `dx1=10.0`: sample interval for the first spatial dimension in meters.
  * `nx1=100`: number of samples for the first spatial dimension.
  * `ox2=0.0`: first sample for the second spatial dimension in meters.
  * `dx2=10.0`: sample interval for the second spatial dimension in meters.
  * `nx2=1`: number of samples for the second spatial dimension.
  * `ox3=0.0`: second sample for the third spatial dimension in meters.
  * `dx3=10.0`: sample interval for the third spatial dimension in meters.
  * `nx3=1`: number of samples for the third spatial dimension.
  * `ox4=0.0`: third sample for the fourth spatial dimension in meters.
  * `dx4=10.0`: sample interval for the fourth spatial dimension in meters.
  * `nx4=1`:number of samples for the fourth spatial dimension.
  * `tau=[1.0, 1.6]`: intercept traveltimes for each event.
  * `p1=[0.0000,-0.0001]
  * `p2=[0.0003, 0.0002]
  * `p3=[-0.0001,-0.0001]
  * `p4=[0.0001,-0.0000]
  * `amp=[1.0,-1.0]`: amplitudes for each parabolic event.
  * `wavelet="ricker"`: wavelet used to model the parabolicr events.
  * `f0=[20.0]`: central frequency of wavelet for each parabolic event.

# Example

```julia
julia> using SeisPlot
julia> d = SeisParabEvents(); SeisPlotTX(d);
```

Credits: Mauricio D Sacchi, 2015
