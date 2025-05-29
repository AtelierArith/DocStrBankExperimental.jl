```
DynamicTreatment{S<:TreatmentSharpness} <: AbstractTreatment
```

Specify an absorbing binary treatment with effects allowed to evolve over time. See also [`dynamic`](@ref).

# Fields

  * `time::Symbol`: column name of data representing calendar time.
  * `exc::Tuple{Vararg{Int}}`: excluded relative time.
  * `s::S`: an instance of [`TreatmentSharpness`](@ref).
