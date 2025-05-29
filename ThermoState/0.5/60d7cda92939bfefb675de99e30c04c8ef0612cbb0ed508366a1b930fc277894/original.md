```
spec(sp::AbstractSpec,val,normalize_units=true)
spec(;kwargs,normalize_units=true)
```

Generates a specification property. It can be called with the keyword interface:

```julia
sp = spec(t=32u"°C")
sp = spec(t=32u"°C",normalize_units = true)
```

Or the positional argument interface:

```julia
sp = spec(Types.Temperature(),32u"°C")
sp = spec(Types.Temperature(),32u"°C",true)
```

If `normalize_units` is set to false, then any unitful quantities are stored as-is, instead of being transformed to SI units.

You can use the @spec_str macro to call the apropiate `Spec` type:

```julia
sp = spec(spec"t",32u"°C")
sp = spec(spec"t",32u"°C",true)
```
