```
derivative_method(pref::DependentParameterRef)::NonGenerativeDerivativeMethod
```

Returns the numerical derivative evaluation method employed with `pref` when it  is used as an operator parameter in a derivative.

**Example**

```julia-repl
julia> derivative_method(pref) 
FiniteDifference
```
