```
TimeDimension <: NonFrequencyDimension <: NMRDimension
```

Abstract supertype for time dimensions used in NMRData objects. Concrete types `T1Dim`, `T2Dim`, `T3Dim` and `T4Dim` are generated for time-domains representing frequency evolution, and `TrelaxDim` and `TkinDim` are generated for representing relaxation and real-time kinetics.
