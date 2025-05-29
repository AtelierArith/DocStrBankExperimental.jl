```
@Loggable(defun)
```

Generate two methods from a function definition (`defun`).

# Notes

Function definition with macro `@Loggable` will generate two methods with the same name (generic function). For example,

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
