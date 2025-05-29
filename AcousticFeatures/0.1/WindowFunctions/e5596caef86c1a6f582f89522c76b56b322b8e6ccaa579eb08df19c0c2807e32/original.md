```
bartlett(N::Int, T::DataType=Float32) -> AbstractArray
Sidelobe peak attenuation = 26.5dB
```

Bartlett window is very similar to a triangular window as returned by the triang function. However, the Bartlett window always has zeros at the first and last samples, while the triangular window is nonzero at those points.
