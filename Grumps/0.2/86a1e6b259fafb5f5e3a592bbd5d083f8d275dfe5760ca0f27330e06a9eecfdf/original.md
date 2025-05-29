```
Data( 
    e                   :: GrumpsEstimator,
    ss                  :: Sources,
    v                   :: Variables,
    microintegrator     :: MicroIntegrator = DefaultMicroIntegrator(),
    macrointegrator     :: MacroIntegrator = DefaultMacroIntegrator(),
    T                   :: Type = F64,
    options             :: DataOptions = GrumpsDataOptions(),
    replicable          :: Bool = true
    )
```

Takes user inputs and converts them into an object that Grumps can understand.  This is synonymous with GrumpsData(...).

*Data* takes the following arguments, of which the first three are mandatory:

  * *e*:                   estimator; see [Estimator choice](@ref)
  * *ss*:                  data sources; see [Data entry](@ref)
  * *v*:                   variables to be used; see [Data entry](@ref)
  * *o*:                   optimization options to be used
  * *microintegrator*:     micro integrator see [Choice of integration method (integrators)](@ref)
  * *macrointegrator*:     macro integrator see [Choice of integration method (integrators)](@ref)
  * *T*:                   floating point type; not heavily tested
  * *u*:                   not yet implemented
  * *options*:             data options to be used, see [Data storage options](@ref)
  * *replicable*:          whether results must be replicable (slows down speed of data creation if set to true)
