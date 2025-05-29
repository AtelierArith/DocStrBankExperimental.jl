```
temperature(model,state::ThermodynamicState,unit,[options...])::Real
```

Keyword symbols: `:t`, `:T`

Compute the temperature (K), from or using the specifications as base.

If you need unitful units, use the macro `@to_units` before the function call
