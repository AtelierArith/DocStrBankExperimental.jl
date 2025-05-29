```
 wave = cwt(Y::AbstractArray{T,N}, c::CWT{W, S, WT}, daughters, rfftPlan =
         plan_rfft([1]), fftPlan = plan_fft([1])) where {N, T<:Real,
                                                         S<:Real,
                                                         U<:Number,
                                                         W<:WaveletBoundary,
                                                         WT<:ContWaveClass}
```

return the continuous wavelet transform along the first axis with averaging.   `wave`, is (signalLength)×(nscales+1)×(previous dimensions), of type `T` of   `Y`. `averagingLength` defines the number of octaves (powers of 2) that are   replaced by an averaging function. This has form `averagingType`, which can be   one of `Father()` or `Dirac()`- in the `Father()` case, it uses the same form   as for the wavelets, while the `Dirac` uses a constant window. If you have   sampling information, you will need to scale wave by δt^(1/p). The default   assumption is that the sampling rate is 2kHz.
