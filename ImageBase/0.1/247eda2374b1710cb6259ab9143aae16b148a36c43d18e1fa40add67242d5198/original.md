```
minimum_finite([f=identity], A; kwargs...)
```

Calculate `minimum(f, A)` while ignoring any values that are not finite, e.g., `Inf` or `NaN`.

If `A` is a colorant array with multiple channels (e.g., `Array{RGB}`), the `min` comparison is done in channel-wise sense.

The supported `kwargs` are those of `minimum(f, A; kwargs...)`.
