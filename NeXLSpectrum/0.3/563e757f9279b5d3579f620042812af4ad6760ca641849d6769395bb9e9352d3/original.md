```
detectorresponse(det::EDSDetector, eff::DetectorEfficiency, incidence::Float64=π/2)::AbstractMatrix
```

Build a matrix which models the detector response including aspects like the detector efficiency, the resolution, the escape peaks.  All the warts that can be modeled within a linear model but not things like coincidence peaks that are non-linear.  This function can (!should!) be specialized for more sophisticated detector models that include more warts.

It also dicretizes the input energies on the same scale as the `EDSDetector` (thus it is square.)  This is reasonable when the detector channel width is much less than the resolution.

Example:

```
genint = computegeneratedintensity(....) # Either characteristic or Bremsstrahlung...
det = simpleEDS(4096, 5.0, 0.0, 132.0, 10)
eff = SDDEfficiency(AP33Tabulation(); thickness=0.0370, deadlayer=30.0e-7, entrance=Film(pure(n"Al"), 10.0e-7))
resp = detectorresponse(det, eff)
# finally compute the measured signal
measured = resp*genint
```
