```
NeXLUncertainties.asa(
    ::Type{DataFrame}, 
    ffr::FilterFitResult; 
    charOnly::Bool=true, 
    material=nothing,
    mc = XPP, fc=ReedFluorescence,
    columns = ( :counts, ) # Selected from ( :roi, :peakback, :counts, :dose )
)::DataFrame
```

Tabulate details about each region-of-interest in the 'FilterFitResult' in a 'DataFrame'.

  * If charOnly then only display characteristic X-ray data (not escapes etc.)
  * If `material` is a Material then the computed k-ratio (KCalc) will also be tabulated along with kmeas/kcalc (KoKCalc).
  * columns - Select optional column outputs (see below)

Columns:

  * Spectrum : UnknownLabel - Identifies the fit spectrum
  * Feature  : Label - Identifies the fit feature (Vector{CharXRay} or other)
  * Reference: String - Name of reference against which :Spectrum was fit over :Feature
  * K : Float64 - The multiplicative fit constant
  * dK : Float64 - The 1σ uncertainty in :K
  * :Start : Int - Start index for fit channels (:roi ∈ columns)
  * :Stop : Int - Stop index for fit channels  (:roi ∈ columns)
  * :Counts : Float64 - Total counts in characteristic peak (peak-back) (:peakback || :counts ∈ columns)
  * :Back : Float64 - Total counts in background under the characteristic peak (:peakback ∈ columns)
  * :PtoB : Float64 - Peak-to-Background assuming 10 eV/channel (:peakback ∈ columns)
  * :KCalc : Float64 - Computed k-ratio assuming a composition. (Requires `material` argument to be specified.)
  * :KoKcalc : Float64 - Ratio of measured/computed k-ratio.  (Requires `material` argument to be specified.)
  * :LiveTime : Float64 - Acquisiton live time (s) (:dose ∈ columns)
  * :ProbeCurrent : Float64 - Probe current (nA) (:dose ∈ columns)
  * :DeadPct : Float64 - Dead time in ProbeCurrent (:dose ∈ columns)
  * :RefCountsPernAs : Float64 - Estimated counts in :Reference in :Feature per unit dose.  (:counts ∈ columns)
  * :CountsPernAs : Float64 - Estimated counts in :Spectrum in :Feature per unit dose.  (:counts ∈ columns)
