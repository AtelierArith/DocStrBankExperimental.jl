```
istft(stft, samplerate, windowsize, hopsize; window)
```

Reconstruct a multichannel audio from its STFT.

# Arguments

  * `stft::Array{Complex{T}, 3}`: the STFT matrix, usually having (1+nfft/2) rows
  * `samplerate::Real`: Sample rate of the resulting audio
  * `windowsize::Int`: window size used for STFT. (default: nfft)
  * `hopsize::Int`: number of frames between STFT columns (default: windowsize/4)
  * `nfft::Int`: the FFT size (default: 2*(size(stft,1)-1))
  * `window::Union{Function, AbstractVector, Nothing}`: function or vector that has the window used for STFT (default: uniform window)
