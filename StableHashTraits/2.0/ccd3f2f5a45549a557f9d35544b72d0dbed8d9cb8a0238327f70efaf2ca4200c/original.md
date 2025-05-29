```
stable_hash(x, context; alg=sha256)
stable_hash(x; alg=sha256, version)
```

Create a stable hash of the given objects. As long as the context remains the same, this hash is intended to remain unchanged across julia versions. The built-in context is HashVersion{N}, and if you specify a `version`, this is equivalent to explicitly passing `HashVersion{version}`.

The version must be explicitly specified: if a new hash version is provided in a future release, your result will *not* change.

You customize how hashes are computed using [`transformer`](@ref).

To change the hash algorithm used, pass a different function to `alg`. It accepts any `sha` related function from `SHA` or any function of the form `hash(x::AbstractArray{UInt8}, [old_hash])`.

The `context` value gets passed as the second argument to [`transformer`](@ref), see [Using Contexts](@ref) for details.

## See Also

[`transformer`](@ref)
