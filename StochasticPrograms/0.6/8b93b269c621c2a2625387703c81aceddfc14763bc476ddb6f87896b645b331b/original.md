```
set_optimizer_attributes(stochasticprogram::StochasticProgram, pairs::Pair...)
```

Given a list of `attribute => value` pairs or a collection of keyword arguments, calls `set_optimizer_attribute(stochasticprogram, attribute, value)` for each pair.

See also: [`get_optimizer_attribute`](@ref)
