```julia
buildHybridManifoldCallbacks(manif)

```

Lots to do here, see RoME.jl #244 and standardized usage with Manifolds.jl.

Notes

  * diffop( test, reference )   <===>   ΔX = inverse(test) * reference

DevNotes

  * FIXME replace with Manifolds.jl #41, RoME.jl #244
