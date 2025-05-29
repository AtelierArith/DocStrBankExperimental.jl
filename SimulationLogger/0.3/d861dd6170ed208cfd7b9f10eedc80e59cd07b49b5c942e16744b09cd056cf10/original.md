```
@log(__LOGGER__, expr)
```

A macro which logs annotated data (based on `expr`) to a privileged data name (`__LOGGER__`). For example,

```julia
@Loggable function dynamics!(dx, x, p, t; kwargs...)
    @log x
    dx = -x
end
```

will generate

```julia
function dynamics!(dx, x, p, t; kwargs...)
    @log x
    dx = -x
end
function dynamics!(dx, x, p, t, __log_indicator__::__LOG_INDICATOR__; kwargs...)
    __LOGGER__ = @isdefined(:__LOGGER__) ? __LOGGER__ : NamedTuple()  # if isdefined, nested logging will work
    @log x
    dx = -x
    return __LOGGER__
end
```

Then, if `@isdefined(__LOGGER__) == false`, just evaluate given experssion `expr`. Otherwise, @log(`expr`) will add a variable to `__LOGGER__` based on `expr`, and also evaluate given experssion `expr`.
