```
SeisGain(d ; <keyword arguments>)
```

Gain a group of traces. Input and output are 2D.

# Arguments

  * `d::Array{Real,2}`: two dimensional data.

# Keyword arguments

  * `dt::Real=0.004`: sampling interval in secs.
  * `kind::AbstractString="time"`: if kind="time", gain = t.^a . * exp(-bt);                        if kind="agc", automatic gain control is applied.
  * `coef::Vector{Real}=[2.0,0.0]`: if kind="time", coef = [a,b];                                  if kind="agc", coef = [agc_gate]
  * `normal::Int=0`: `normal=0` no normalization; `normal=1` normalize each trace by                 amplitude; `normal=2` normalize each trace by rms value/

# Example

```julia
julia> using PyPlot
julia> d = SeisHypEvents();
       dout = SeisGain(d, kind="agc", coef=[0.05]);
       SeisPlotTX([d dout]);
```

Credits:  Aaron Staton Updates: Juan I. Sabbione, Mauricio D. Sacchi, Fernanda Carozzi
