```
register(datadep::AbstractDataDep)
```

Registers the given datadep to be globally available to the program. this makes `datadep"Name"` work. `register` should be run within this `__init__` of your module.
