```
dat = loadrds(fid::IOStream, frame::Int, frsize::Int, ncoil::Int; 
              T::Type{<:Union{Int16,Int32}} = Int16)
```

Load one shot (frame) from MRI data file created with GE's Raw Data Server.

in

  * `fid::IOStream` File handle
  * `frame::Int` Shot/frame number
  * `frsize::Int` Number of data points in each readout (per coil)
  * `ncoil::Int` Number of receive coils

option

  * `T::Type{<:Union{Int16,Int32}} = Int16` for the base type of (complex) data loaded

out

  * `dat::Array{Complex{T}}` `[frsize, ncoil]`
