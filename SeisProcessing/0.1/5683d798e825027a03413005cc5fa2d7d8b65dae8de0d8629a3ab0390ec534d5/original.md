```
SeisFKFilter(in; <keyword arguments>)
```

Removes energy from seismic data by applying filters to a gather in the Frequency-wavenumber domain

# Arguments

  * `in`: 2D input data in TX domain. First dimension is time.

# Keyword arguments

  * `dt=0.004`: time sampling interval in secs.
  * `dx=10`: space sampling interval in meters.
  * `va=-2000,vb=-3000,vc=3000,vd=2000`: apparent velocity corners to filter

# Output

  * `out`: Filtered data in TX domain

# Example

```julia
julia> d = SeisLinearEvents(); df = SeisFKFilter(d,va=-4000.,vb=-6000.,vc=6000.,vd=4000.);
```

*Credits: Aaron Stanton,2017*
