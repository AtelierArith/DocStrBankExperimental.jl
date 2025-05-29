```
extent(sf::SpectrumFeature, det::Detector, ampl::Float64)::Tuple{Float64, Float64}
```

Computes the channel range encompassed by the specified set of x-ray transitions down to an intensity of ampl.  Relative line weights are taken into account.
