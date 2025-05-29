```
call_function(fref::ParameterFunctionRef, support...)::Float64
```

Safely evaluates the [`raw_function`](@ref) of `fref` at a particular support `support` point that matches the format of the infinite parameter tuple given when the `fref`  was defined. This is essentially equivalent to `raw_function(fref)(supps...)`. 
