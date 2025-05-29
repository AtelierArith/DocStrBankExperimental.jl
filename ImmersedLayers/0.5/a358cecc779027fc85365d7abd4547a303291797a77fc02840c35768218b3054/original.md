```
ConstrainedSystems.init(u0,tspan,sys::ILMSystem,[alg=LiskaIFHERK()/HETrapezoidalAB2()])
```

Initialize the integrator for a time-varying immersed-layer system of PDEs, described in `sys`. The default time marching algorithm in the keyword algorithm is chosen automatically based on whether there is an invertible `bc_regulator` operator in the system. If so, then `HETrapezoidalAB2()` is chosen; otherwise, `LiskaIFHERK()` is chosen. Both are second-order accurate. Another choice is `IFHEEuler()`, also suitable for problems with no invertible `bc_regulator` matrix.
