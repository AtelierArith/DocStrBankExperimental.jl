```
RecoPlan{T <: Union{AbstractImageReconstructionParameters, AbstractImageReconstructionAlgorithm}}
```

Configuration template for an image reconstruction algorithm or paremeters of type `T`.  A `RecoPlan{T}` has the same properties with type checking as `T` with the exception that properties can be missing and nested algorithms and parameters can again be `RecoPlan`s.

Plans can be nested and form a tree. A parent plan can be accessed with `parent` and set with `parent!`. Algorithms and parameters can be converted to a plan with `toPlan`.

Plans feature serialization with `toTOML`, `toPlan` and `loadPlan` and the ability to attach callbacks to property changes with `Òbservables` and `on`.
