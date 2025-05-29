```
Sca
```

Abstract type to indicate a scaling from which several other types subtype.

# Possible subtypes

  * `ScaUnit`: No scaling of the indices
  * `ScaNorm`: Total length along each dimension is normalized to 1
  * `ScaMid`: Reaches 1.0 at the borders, if used in combination with `CtrMid`. Useful for keeping real-space symmetry.
  * `ScaFT`: Reciprocal Fourier coordinates compared to Nyquist sampling
  * `ScaFTEdge`: Such that the edge (in FFT sense) of the pixel is 1.0
