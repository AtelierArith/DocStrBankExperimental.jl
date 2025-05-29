```
DetectorHit = NamedTuple{(:evtno, :detno, :thit, :edep, :pos), ...)
```

Representation of an localized energy deposition in a detector.

Use [`DetectorHitEvents`](@ref) for arrays of `DetectorHit` that have a compact memory layout.
