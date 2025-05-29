```
SeisAddNoise(d, snr; <keyword arguments>)
```

Add noise to an N-dimensional input data `d`. Should specify the signal-to-noise ratio level `snr`. Noise can be band limited using kewyord `L`.

# Arguments

  * `d::Array{Real, N}`: N-dimensional data.
  * `snr::Real`: signal-to-noise ratio.
  * `db::Bool=false`: Flag is false if snr is given by amplitude. Flag is true if

snr is given in dB.

  * `pdf::AbstractString="gaussian"`: random noise probability distribution:

`"gaussian"` or `"uniform"`.

  * `L::Int=1`: averaging operator length to band-limit the random noise.

# Examples

```julia
julia> using PyPlot
julia> w = Ricker(); wn = SeisAddNoise(w, 2); plot(w); plot(wn);
MeasureSNR(w, wn)
julia> d = SeisHypEvents(); dn = SeisAddNoise(d, 1.0, db=true, L=9);
SeisPlotTX([d dn]); MeasureSNR(d, dn, db=true)
```

Credits: Juan I. Sabbione, 2016
