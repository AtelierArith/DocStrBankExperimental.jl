```
bohman(N::Int, T::DataType=Float32) -> AbstractArray
Sidelobe peak attenuation = 46dB
```

Bohman window is the convolution of two half-duration cosine lobes. In the time domain, it is the product of a triangular window and a single cycle of a cosine with a term added to set the first derivative to zero at the boundary. Bohman windows fall off as 1/ω⁴
