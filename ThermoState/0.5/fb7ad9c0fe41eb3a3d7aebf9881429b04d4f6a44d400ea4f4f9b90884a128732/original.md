```
quality(model,state::ThermodynamicState)::NamedTuple
```

Keyword symbols: `:quality`

Returns the vapor quality stored in the state

Returns NaN otherwise.

This function is an alias for `mass_vapor_fraction`.
