```
sound(x::AbstractVector, S::Real = framerate(x), args...; kwargs...)
```

Play monophonic audio signal `x` at sampling rate `S` samples per second through default audio output device using the `PortAudio` package. Caller must specify `S` unless a `framerate` method is defined for `x`.
