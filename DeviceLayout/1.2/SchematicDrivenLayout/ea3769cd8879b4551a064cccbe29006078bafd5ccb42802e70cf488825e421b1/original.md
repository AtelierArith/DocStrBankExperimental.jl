```
render!(
    cs::AbstractCoordinateSystem,
    sch::Schematic,
    target::LayoutTarget;
    strict=:error,
    kwargs...
)
```

Render the schematic `sch` to `cs` using `target`'s rendering options, without modifying `sch`.

Users must run `check!(sch)` before calling this method; otherwise, it will throw an error.

The `strict` keyword should be `:error`, `:warn`, or `:no`.

The `strict=:error` keyword option causes `render!` to throw an error if any errors were logged while building component geometries or while rendering geometries to `cs`. This is enabled by default, but can be disabled with `strict=:no`, in which case any component which was not successfully built will have an empty geometry, and any non-fatal rendering errors will be ignored as usual. Using `strict=:no` is recommended only for debugging purposes.

The `strict=:warn` keyword option causes `render!` to throw an error if any warnings were logged. This is disabled by default. Using `strict=:warn` is suggested for use in automated pipelines, where warnings may require human review.
