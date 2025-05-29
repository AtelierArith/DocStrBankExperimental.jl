```
geoEff(detector::Detector = Detector(), aSource::Tuple{Point, Real, Real} = source())::Float64
```

same as `geoEff(::Detector, ::Point, ::Real, ::Real)` but splatting the argument  in the Tuple `aSource`.

!!! note
    in the case of both no detector and no source Tuple or just the source Tuple is not supplied, it prompt the user to input a source (and detector) via the `console`.

