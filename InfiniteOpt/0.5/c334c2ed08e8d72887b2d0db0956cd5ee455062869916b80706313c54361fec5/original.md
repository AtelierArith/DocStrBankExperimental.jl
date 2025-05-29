```
set_derivative_method(pref::DependentParameterRef, 
                      method::NonGenerativeDerivativeMethod)::Nothing
```

Specfies the desired derivative evaluation method `method` for derivatives that are  taken with respect to `pref`. Errors if `method` is generative (i.e., it requires  the definition of additional supports)

**Example**

```julia-repl
julia> set_derivative_method(d, FiniteDifference())

```
