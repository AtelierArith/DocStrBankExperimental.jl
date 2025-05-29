```
Config(; kw...)
Config(::AbstractDict)
```

A wrapper around an `OrderedDict{Symbol, Any}` with the special properties:

1. You can get/set items via `getproperty`/`setproperty!`:

    c = Config()  c.one = 1  c.one == 1
2. Properties that don't exist will be created on the fly:

    c = Config()  c.one.two.three = "neat!"
