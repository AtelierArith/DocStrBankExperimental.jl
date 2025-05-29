```
Iteration(;
    mc::Type{<:MatrixCorrection} = XPP,
    fc::Type{<:FluorescenceCorrection} = ReedFluorescence,
    cc::Type{<:CoatingCorrection} = Coating,
    updater = WegsteinUpdateRule(),
    converged = RMSBelowTolerance(0.00001),
    unmeasured = NullUnmeasuredRule(),
)
```

Collects the information necessary to define the iteration process including the `MatrixCorrection` and `FLuorescenceCorrection` algorithms, the iteration `UpdateRule`, the `ConvergenceTest`, and an `UnmeasuredElementRule`.
