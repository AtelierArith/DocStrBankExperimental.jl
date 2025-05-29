```
maximum_finite([f=identity], A; kwargs...)
```

Calculate `maximum(f, A)` while ignoring any values that are not finite, e.g., `Inf` or `NaN`.

If `A` is a colorant array with multiple channels (e.g., `Array{RGB}`), the `max` comparison is done in channel-wise sense.

The supported `kwargs` are those of `maximum(f, A; kwargs...)`.
