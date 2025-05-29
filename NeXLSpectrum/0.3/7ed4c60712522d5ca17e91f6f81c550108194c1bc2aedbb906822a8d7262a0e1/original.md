```
Resolution
```

An abstract type describing the channel dependence of the resolution of an EDS detector.

Implements:

```
resolution(eV::Float64, res::Resolution)::Float # Resolution at specified energy
profile(energy::Float64, xrayE::Float64, res::Resolution) # Amplitude for a signal at the specified energy at the specified energy
extent(xrayE::Float64, res::Resolution, ampl::Float64)::Tuple{2,Float} # The range of channels over which the signal exceeds ampl
```
