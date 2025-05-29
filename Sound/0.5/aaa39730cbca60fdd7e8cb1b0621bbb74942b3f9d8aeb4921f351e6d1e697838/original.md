```
sound(x::AbstractMatrix, S::Real = framerate(x) [, output_device])
```

Play stereo audio signal `x` at sampling rate `S` samples per second through default audio output device using the `PortAudio` package. Caller must specify `S` unless a `framerate` method is defined for `x`.
