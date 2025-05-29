```
Sync(assets...)
```

A group ("block") of assets that will be imported sequentially (synchronously) in the browser. This is useful when dependencies have side effects that must be executed in order. The elements of `assets` may either be [`Asset`](@ref)s themselves, any valid constructor for an [`Asset`](@ref), or a [`Sync`](@ref) or [`Async`](@ref).

If the imports do not need to be imported sequentially, use [`Async`](@ref) instead.

# Examples

```julia-repl
julia> WebIO.Sync(Asset("foo.js"), "bar" => "bar.js")
Sync(Asset[Asset("js", nothing, "foo.js"), Asset("js", "bar", "bar.js")])
```
