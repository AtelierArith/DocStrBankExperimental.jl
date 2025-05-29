```
SeisSincInterp1D(d,order)
```

Resample seismic traces via 1D sinc interpolation. The time series are sampled every dt secs,  the output corresponds to series with time interval dt/`order`.

# Arguments

  * `d::Array{Real,N}`: N-dimensional data, first dimension is time
  * `order::Integer`: order of interpolation 2,4

# Examples

2-time upsampling of a wavelet

```julia
julia> order = 2; dt=0.004; w = Ricker(dt=dt, f0=20); t = collect(0:1:length(w)-1)*dt;
julia> wout = SeisSincInterp1D(w,order); tout = collect(0:1:length(wout)-1)*dt/order;
julia> plot(t,w); plot(tout,wout,"*")
```

4-time upsampling of a gather

```julia
julia> d = SeisLinearEvents(); di = SeisSincInterp1D(d,4);
julia>  SeisPlotTX(d,style="wiggles")
julia>  SeisPlotTX(di,style="wiggles")  
```

MAY 2018, MDS
