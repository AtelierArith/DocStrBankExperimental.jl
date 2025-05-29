```
barthann(N::Int, T::DataType=Float32) -> AbstractArray
Sidelobe peak attenuation = 35.9dB
```

barthann window has a mainlobe at the origin and asymptotically decaying sidelobes on both sides. It is a linear combination of weighted Bartlett and Hanning windows with near sidelobes lower than both Bartlett and Hanning and with far sidelobes lower than both Bartlett and Hamming windows. The mainlobe width of the modified Bartlett-Hann window is not increased relative to either Bartlett or Hann window mainlobes.
