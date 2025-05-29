```
MultistartFit(DM::AbstractDataModel; maxval::Real=1e5, MultistartDomain::HyperCube=FullDomain(pdim(DM), maxval), kwargs...)
```

Performs Multistart optimization with `N` starts and timeout of fits after `timeout` seconds. If `resampling=true`, if likelihood non-finite new initial starts are redrawn until `N` suitable initials are found.  If `Robust=true`, performs optimization wrt. p-norm according to given kwarg `p`. For `Full=false`, only the final MLE is returned, otherwise a `MultistartResults` object is returned, which can be further analyzed and plotted. The keyword `TransformSample` can be used to specify a function which is applied to the sample, allowing e.g. for sampling only a subset of the parameters and then adding on components which should stay at fixed initial values for the multistart.

!!! note
    Any further keyword arguments are passed through to the optimization procedure [`InformationGeometry.minimize`](@ref) such as tolerances, optimization methods, domain constraints, etc.

