```
Detector(CryRadius::Real, CryLength::Real, HoleRadius::Real, HoleDepth::Real)
```

construct and return `well-type`, `bore-hole` or `cylindrical` detector according to the arguments.  it inspect the arguments and call the appropriate leaf type constructor.

!!! note
    if the value(s) of the last argument(s) is\are `zero`, it acts as a missing argument(s).


**see also:** [`CylDetector`](@ref), [`BoreDetector`](@ref), [`WellDetector`](@ref).
