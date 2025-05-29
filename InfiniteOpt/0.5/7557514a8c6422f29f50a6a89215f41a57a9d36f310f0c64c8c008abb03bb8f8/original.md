```
call_function(fref::GeneralVariableRef, support...)::Float64
```

Call the parameter function of `fref` at `support`. An `ArgumentError` is thrown if `fref` is not a parameter function.
