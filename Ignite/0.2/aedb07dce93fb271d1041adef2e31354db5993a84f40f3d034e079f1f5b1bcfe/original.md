```julia
every_filter(
    every::Union{Int64, AbstractVector{Int64}}
) -> Union{Ignite.EveryFilter{Int64}, Ignite.EveryFilter{T} where T<:AbstractVector{Int64}}

```

Creates an event filter function for use in a `FilteredEvent` that returns `true` periodically depending on `every`:

  * If `every = n::Int`, the filter will trigger every `n`th firing of the event.
  * If `every = Int[n₁, n₂, ...]`, the filter will trigger every `n₁`th firing, every `n₂`th firing, and so on.
