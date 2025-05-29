```
calc(detector::Detector = Detector(), aSource::Tuple{Point, Float64, Float64,} = source())
```

calculate and display on the `console` the `geometrical efficiency` of the  detector `detector` for the tuple `aSource` describing the source.

**`Throw`** an  `inValidGeometry` if the source location is inappropriate.

**see also:** [`geoEff(::Detector, ::Tuple{Point, Float64, Float64})`](@ref)

!!! note
    if source description `aSource` alone or even both source description and detector `detect`   are missing, the method prompt the user to complete the missing data via the `console`.

