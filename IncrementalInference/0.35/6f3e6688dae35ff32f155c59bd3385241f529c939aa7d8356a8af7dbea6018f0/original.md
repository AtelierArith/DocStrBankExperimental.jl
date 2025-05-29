```julia
sampleFactor(cf)
sampleFactor(cf, N)

```

Sample the factor stochastic model `N::Int` times and store the samples in the preallocated `ccw.measurement` container.

DevNotes

  * Use in place operations where possible and remember `measurement` is a `::Tuple`.
  * TODO only works on `.threadid()==1` at present, see #1094
  * Also see, JuliaRobotics/RoME.jl#465
