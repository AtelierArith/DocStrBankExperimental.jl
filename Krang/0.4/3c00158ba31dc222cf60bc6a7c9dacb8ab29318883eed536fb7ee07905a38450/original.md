```julia
struct SlowLightIntensityCamera{T, A} <: Krang.AbstractCamera
```

Camera that caches slow light raytracing information for an observer sitting at radial infinity. The frame of this observer is alligned with the Boyer-Lindquist frame.
