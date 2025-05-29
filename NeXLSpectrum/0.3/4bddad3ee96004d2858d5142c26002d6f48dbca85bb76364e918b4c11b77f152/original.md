```
fit_spectrum(unk::Spectrum{T}, drefs::DirectReferences)::DirectFitResult{T} where { T <: Real }
```

Fits the direct references to the unknown spectrum returning a `DirectFitResult` struct containing k-ratios and other output quantities from the fit.

Surprisingly, this function requires that `unk[:Composition]` is defined as a `Material` with an estimate of the composition of the material from which `unk` was collected.  This information is necessary to model the continuum background.  Yes, this seems circular (and it is.)  One option is to perform a filter-fit first, quantify the filter fit and then use this as your estimate.
