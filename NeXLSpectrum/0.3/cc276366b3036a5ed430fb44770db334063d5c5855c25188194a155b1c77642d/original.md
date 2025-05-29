```
matches(spec::Spectrum, det::Detector, tol::Float64 = 1.0)::Bool
matches(spec1::Spectrum, spec2::Spectrum, tol::Float64 = 1.0)::Bool
```

Does the calibration of the Spectrum (approximately) match the calibration of the Detector or the other Spectrum?
