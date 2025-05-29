```
getLastValue(model::InstantiatedModel, name::String; unit=true)
```

Return the last stored value of variable `name` from `model`. If `unit=true` return the value with its unit, otherwise with stripped unit.

If `name` is not known or no result values yet available, an info message is printed and the function returns `nothing`.

`name` can be a time-varying variable or a parameter.
