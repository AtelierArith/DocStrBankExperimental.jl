```
set_derivative_method(pref::IndependentParameterRef, 
                      method::AbstractDerivativeMethod)::Nothing
```

Specfies the desired derivative evaluation method `method` for derivatives that are  taken with respect to `pref`. Any internal supports exclusively associated with  the previous method will be deleted. Also, if any derivatives were evaluated  manually, the associated derivative evaluation constraints will be deleted. Errors  if new derivative method generates supports that are incompatible with existing  measures.

**Example**

```julia-repl
julia> set_derivative_method(d, OrthogonalCollocation(2))

```
