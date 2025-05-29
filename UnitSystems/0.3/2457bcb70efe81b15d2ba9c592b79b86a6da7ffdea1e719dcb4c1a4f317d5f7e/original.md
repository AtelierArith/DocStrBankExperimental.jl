```
UnitSystems.similitude() = haskey(ENV,"SIMILITUDE")
```

An optional environment variable `ENV["SIMILITUDE"]` induces `UnitSystems.similitude()` to return `true`, giving flexibility for building dependencies whenever it is desirable to toggle usage between `UnitSystems` (default) and `Similitude` (requires environment variable specification). For example, in `MeasureSystems` and `Geophysics` this option is used to increase flexibility with variety in local compilation workflow.
