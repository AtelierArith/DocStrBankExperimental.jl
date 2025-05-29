```
piecewise_linear_interpolate(waveform;[max_vale=Inf64,max_slope=Inf64,min_step=0.0])
```

Function which takes a waveform and translates it to a linear interpolation subject to some constraints. The function returns a piecewise linear waveform. if the Waveform is piecewise linear only the constraints will be checked. 

# Arguments

  * `waveform`: ['Waveform'](@ref)  to be discretized.

# Keyword Arguments

  * `min_step`: minimum possible step used in interpolation
  * `max_slope`: Maximum possible slope used in interpolation
  * `atol`: tolerance of interpolation, this is a bound to the area between the linear interpolation and the waveform.
