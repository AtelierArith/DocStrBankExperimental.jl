```
space_index(::Val{:index}, jd::Number; kwargs...) -> Number
space_index(::Val{:index}, date::DateTime; kwargs...) -> Number
```

Get the space `index` for the Julian day `jd` or the `instant`. The latter must be an object of type `DateTime`. `kwargs...` can be used to pass additional configuration for the space index.
