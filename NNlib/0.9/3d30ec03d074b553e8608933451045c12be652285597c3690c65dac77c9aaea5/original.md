```
spectrogram(waveform;
    pad::Int = 0, n_fft::Int, hop_length::Int, window,
    center::Bool = true, power::Real = 2.0,
    normalized::Bool = false, window_normalized::Bool = false,
)
```

Create a spectrogram or a batch of spectrograms from a raw audio signal.

# Arguments

  * `pad::Int`:   Then amount of padding to apply on both sides.
  * `window_normalized::Bool`:   Whether to normalize the waveform by the window’s L2 energy.
  * `power::Real`:   Exponent for the magnitude spectrogram (must be ≥ 0)   e.g., `1` for magnitude, `2` for power, etc.   If `0`, complex spectrum is returned instead.

See [`stft`](@ref) for other arguments.

# Returns

Spectrogram in the shape `(T, F, B)`, where `T` is the number of window hops and `F = n_fft ÷ 2 + 1`.
