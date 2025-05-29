Defines a FIRBasisfunction which can be called for each event, defining the time-expanded basis kernel

```julia
mutable struct FIRBasis <: Unfold.BasisFunction
```

  * `times`: vector of times along rows of kernel-output (in seconds)
  * `name`: name of the event, should be the actual eventName in `eventcolumn` of the dataframes later
  * `shift_onset`: by how many samples do we need to shift the event onsets? This number is determined by how many 'negative' timepoints the basisfunction defines
  * `interpolate`: should we linearly interpolate events not on full samples?
  * `scale_duration`: should we scale kernel to the duration? If yes, with which method

(tipp: most users would you want to call firbasis, not generate it manually)

# Examples

```julia-repl
julia>  b = FIRBasis(range(0,1,length=10),"basisA",-1)
```
