```
Detector
```

An abstract type defining the characteristics of an X-ray detector.

Implements:

```
channelcount(det::Detector)::Int
scale(det::Detector)::EnergyScale
resolution(eV::Float64, det::Detector)::Float64 # FWHM at eV
energy(ch::Int, det::Detector)::Float64
channel(eV::Float64, det::Detector)::Int
profile(energy::Float64, xrayE::Float64, det::Detector)
lld(det::Detector)::Int
isvisible(sf::SpectrumFeature, det::Detector)
```
