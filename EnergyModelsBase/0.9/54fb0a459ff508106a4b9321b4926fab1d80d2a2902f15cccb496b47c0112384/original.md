```
ResourceEmit{T<:Real} <: Resource
```

Resources that can be emitted (*e.g.*, CO₂, CH₄, NOₓ).

These resources can be included as resources that are emitted, *e.g*, in the variable [`emissions_strategic`](@ref man-opt_var-emissions).

# Fields

  * **`id`** is the name/identifyer of the resource.
  * **`co2_int::T`** is the CO₂ intensity, *e.g.*, t/MWh.
