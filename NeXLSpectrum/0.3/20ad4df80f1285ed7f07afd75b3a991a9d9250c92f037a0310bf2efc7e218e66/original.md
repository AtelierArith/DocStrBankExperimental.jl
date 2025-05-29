```
filterfit(unk::FilteredUnknownW, ffs::AbstractVector{FilteredReference}, forcezeros = true)::FilterFitResult
```

Filter fit the unknown against ffs, an array of FilteredReference and return the result as an FilterFitResult object. By default use the generalized LLSQ fitting (pseudo-inverse implementation).

This function is designed to reperform the fit if one or more k-ratio is less-than-or-equal-to zero.  The FilteredReference corresponding to the negative value is removed from the fit and the fit is reperformed. How the non-positive value is handled is determine by forcezeros. If forcezeros=true, then the returned k-ratio for the non-positive value will be set to zero (but the uncertainty remains the fitted one).  However, if forcezeros=false, then the final non-positive k-ratio is returned along with the associated uncertainty.  forcezeros=false is better when a number of fit k-ratio sets are combined to produce an averaged k-ratio with reduced uncertainty. forcezeros=true would bias the result positive.
