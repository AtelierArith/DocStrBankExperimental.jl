```
SeisEnvelope(in; <keyword arguments>)
```

Calculate the envelope attribute of a group of input traces.

# Arguments

  * `in`: input data. A 2D Array where the first dimension is time.

# Example

```julia
julia> using PyPlot
julia> dtsec = 0.002; w = Ricker(dt=dtsec);
julia> e = SeisEnvelope(w); t=dtsec*collect(0:1:length(w)-1);plot(t,w,t,e,"-r");xlabel("Time [s]")
```

*Credits: Aaron Stanton,2017*
