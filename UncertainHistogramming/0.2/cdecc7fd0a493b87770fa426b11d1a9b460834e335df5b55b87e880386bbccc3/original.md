```
setindex!(::ContinuousHistogram, val, ::Type{<: Moment})
```

Convenience function for accessing the [`ContinuousHistogram`](@ref) [`Moment`](@ref)s from their name.

!!! warning
    This functionality should only be used internally as modifying the [`ContinuousHistogram`](@ref) `moments` directly would invalidate the [`push!`](@ref) pipeline and ultimately the statistics.

    But it's here if you need it for some `dev` reason.

