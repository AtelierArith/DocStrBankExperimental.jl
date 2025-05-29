```julia
struct IntensityCamera{T, A} <: Krang.AbstractCamera
```

Camera that caches fast light raytracing information for an observer sitting at radial infinity. The frame of this observer is alligned with the Boyer-Lindquist frame.
