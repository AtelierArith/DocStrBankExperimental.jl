```
model_spectrum(f, h, args...; kwargs...)
```

# Arguments:

  * `f`: the model-estimation function, e.g., `ar,arma`
  * `h`: The sample time
  * `args`: arguments to `f`
  * `kwargs`: keyword arguments to `f`

# Example:

```
using ControlSystemIdentification, DSP
T = 1000
s = sin.((1:T) .* 2pi/10)
S1 = spectrogram(s,window=hanning)
estimator = model_spectrum(ar,1,2)
S2 = spectrogram(s,estimator,window=rect)
plot(plot(S1),plot(S2)) # Requires the package LPVSpectral.jl
```
