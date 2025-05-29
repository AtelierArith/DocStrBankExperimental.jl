```
getDetectors(detectors_array::Vector{<:Detector} = Detector[])::Vector{Detector}
```

return the `detectors_array` as Vector{Detector} extended by the entered detectors and sorted according to the  detector volume.  prompt the user to input detector parameters from the `console`.

!!! note
    If no array received in the input an empty array will be created to receive the converted detectors.

