```
melspectrogram(s, n=div(length(s), 8), args...; fs=1, nmels::Int=128, fmin::Real=0.0f0, fmax::Real=fs / 2.0f0, window=hanning, kwargs...)
```

DOCSTRING

#Arguments:

  * `s`: signal
  * `n`: number of points in each window
  * `args`: are sent to `spectrogram`
  * `fs`: sample frequency
  * `nmels`: number of mel frequencies
  * `fmin`: minimum freq
  * `fmax`: maximum freq
  * `window`: window function, defaults to hanning
  * `kwargs`: are sent to `spectrogram`
