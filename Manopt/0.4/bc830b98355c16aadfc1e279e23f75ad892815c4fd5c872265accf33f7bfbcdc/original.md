```
AbstractQuasiNewtonDirectionUpdate
```

An abstract representation of an Quasi Newton Update rule to determine the next direction given current [`QuasiNewtonState`](@ref).

All subtypes should be functors, they should be callable as `H(M,x,d)` to compute a new direction update.
