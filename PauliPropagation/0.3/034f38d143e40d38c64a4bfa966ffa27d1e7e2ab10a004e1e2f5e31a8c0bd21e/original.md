```
estimatemse!(circ, pstr::PauliString, error_array::AbstractVector, thetas, split_probabilities; stateoverlapfunc=overlapwithzero, circuit_is_reversed=false, kwargs...)
```

In-place version of `estimatemse`. This function takes an array `error_array` of length `n_mcsamples` as an argument and modifies it in-place.  It further assumes that the `thetas` and `split_probabilities` are already correctly calculated and provided as arguments.  In general they will be vectors, but they can also be real numbers. A custom truncation function can be passed as `customtruncfunc` with the signature `customtruncfunc(pstr::PauliStringType, coefficient)::Bool`.
