```
power(p)
```

For a `Periodogram`, returns the computed power at each frequency as a Vector.

For a `Spectrogram`, returns the computed power at each frequency and time bin as a Matrix. Dimensions are frequency × time.

For a `CrossPowerSpectra`, returns the pairwise power between each pair of channels at each frequency. Dimensions are channel x channel x frequency.
