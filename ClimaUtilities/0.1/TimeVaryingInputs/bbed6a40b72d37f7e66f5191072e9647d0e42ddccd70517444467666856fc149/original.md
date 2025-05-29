```
TimeVaryingInput(func)
TimeVaryingInput(times, vals; method, context)
```

Construct on object that knows how to evaluate the given function/data on the model times.

# When passing a function

When a function `func` is passed, the function has to be GPU-compatible (e.g., no splines).

# When passing single-site data

When a `times` and `vals` are passed, `times` have to be sorted and the two arrays have to have the same length.

======= When the input is a function, the signature of the function can be `func(time, args...; kwargs...)`. The function will be called with the additional arguments and keyword arguments passed to `evaluate!`. This can be used to access the state and the cache and use those to set the output field.

For example:

```julia
CO2fromp(time, Y, p) = p.atmos.co2
input = TimeVaryingInput(CO2fromY)
evaluate!(dest, input, t, Y, p)
```
