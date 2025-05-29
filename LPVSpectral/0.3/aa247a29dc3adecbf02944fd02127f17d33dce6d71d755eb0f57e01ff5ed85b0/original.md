```
mfcc(s, args...; nmfcc::Int=20, nmels::Int=128, window=hanning, kwargs...)
```

Compute the [Mel-frequency cepstral coefficients (MFCCs)](https://en.wikipedia.org/wiki/Mel-frequency_cepstrum)

# Arguments:

  * `s`: signal
  * `args`: are sent to `spectrogram`
  * `nmfcc`: number of coeffs
  * `nmels`: number of mel frequencies
  * `window`: window function, defaults to hanning
  * `kwargs`: are sent to `spectrogram`
