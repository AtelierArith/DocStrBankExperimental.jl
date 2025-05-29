```
@f(func,a,b,c,...)
```

This macro is an alias to

```
func(model, V, T, z, a, b, c, ...)
```

where `func` is the name of the function, `model` is the model struct, `V` is the volume, `T` is the absolute temperature, `z` is an array of number of moles of each component, and `a`, `b`, `c`, ... are arbitrary parameters that get passed to `func`.

It is very common for functions that are involved in the models to contain the `model`, `V`, `T` and `z` parameters, so this macro helps reduce code repetition as long as the first four parameters in the function are written exactly as above.
