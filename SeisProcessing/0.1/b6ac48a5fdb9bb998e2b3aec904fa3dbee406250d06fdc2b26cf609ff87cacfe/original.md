```
SeisDiff(d ; <keyword arguments>)
```

Apply differentiation to seismic traces in freq. It can also be used to apply a phase rotation

# Arguments

  * `d`: Input 2D data array in tx domain. First dimension is time.

# Keyword arguments

  * `delay=0.1`: desired time delay in seconds.
  * `pow=-2`: order of derivative
  * `rot=0`: constant phase shift or rotation

# Example

```
julia> d = SeisLinearEvents(); SeisPlotTX(d);
julia> d2 = SeisDiff(d;dt=0.004,pow=1); SeisPlotTX(d);
```
