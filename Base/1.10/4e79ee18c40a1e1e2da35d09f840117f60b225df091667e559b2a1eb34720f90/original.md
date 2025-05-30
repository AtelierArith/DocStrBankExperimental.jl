```
which(f, types)
```

Returns the method of `f` (a `Method` object) that would be called for arguments of the given `types`.

If `types` is an abstract type, then the method that would be called by `invoke` is returned.

See also: [`parentmodule`](@ref), and `@which` and `@edit` in [`InteractiveUtils`](@ref man-interactive-utils).
