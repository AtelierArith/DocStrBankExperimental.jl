```
set_derivative_method(pref::GeneralVariableRef,
                      method::AbstractDerivativeMethod
                      )::Nothing
```

Specify the numerical derivative evaluation technique associated with `pref`. An `ArgumentError` is thrown if `pref` is not an infinite parameter.
