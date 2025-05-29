```julia
function goertzel_fast( x  :: AbstractVector{T},
                        wl :: Int,
                        a  :: Real,
                        c  :: Real,
                        s  :: Real,
                        d  :: Real,
                    startAT:: Int = 1) where T<:Union{Real, Complex}
```

Fast version of the [`goertzel`](@ref) function to be preferred if the function is invoked repeatedly and speed is of concern. The user provides as arguments:

  * a time series as input vector `x`,
  * `wl`, the number of samples in `x` (or the window length),
  * `a` = $2/wl$,
  * `c` = $cos(p)$ where $p$=`2*π*round(UInt16, (f*wl)/sr)/wl`, $f$ is the desired frequency and $sr$ the sampling rate,
  * `s` = $sin(p)$
  * `d` = 2*`c`
  * `startAt` as in the [`goertzel`](@ref) function.

**See also**: [`goertzel`](@ref), [`goertzel2`](@ref).
