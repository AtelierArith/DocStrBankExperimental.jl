```julia
once_filter(
    once::Union{Int64, AbstractVector{Int64}}
) -> Union{Ignite.OnceFilter{Int64}, Ignite.OnceFilter{T} where T<:AbstractVector{Int64}}

```

Creates an event filter function for use in a `FilteredEvent` that returns `true` at specific points depending on `once`:

  * If `once = n::Int`, the filter will trigger only on the `n`th firing of the event.
  * If `once = Int[n₁, n₂, ...]`, the filter will trigger only on the `n₁`th firing, the `n₂`th firing, and so on.
