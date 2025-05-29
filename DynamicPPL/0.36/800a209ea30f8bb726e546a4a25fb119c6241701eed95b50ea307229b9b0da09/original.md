```
LogDensityFunction(
    ldf::LogDensityFunction,
    adtype::Union{Nothing,ADTypes.AbstractADType}
)
```

Create a new LogDensityFunction using the model, varinfo, and context from the given `ldf` argument, but with the AD type set to `adtype`. To remove the AD type, pass `nothing` as the second argument.
