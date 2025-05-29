```
@affineunit(symb, abbr, offset)
```

Macro for easily defining affine units. `offset` gives the zero of the relative scale in terms of an absolute scale; the scaling is the same as the absolute scale. Example: `@affineunit °C "°C" (27315//100)K` is used internally to define degrees Celsius.

!!! compat "Unitful 1.10"
    Documenting the resulting unit by adding a docstring before the `@affineunit` call requires Unitful 1.10 or later.

