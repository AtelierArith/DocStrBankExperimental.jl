```
produce(x)
```

When run inside a [`TapedTask`](@ref), will immediately yield to the caller, returning value `x`. Users will typically hit this function when calling `consume`.

See also: [`Libtask.consume`](@ref)
