Special format that overrides the current context.

In particular, packing (or similarly unpacking) via

```
pack(val, ContextFormat{C, F}(), C2())
```

is equivalent to

```
pack(val, F(), C())
```

where the original context `C2 <: Context` is ignored.

This format is, for example, useful in combination with [`fieldformats`](@ref), to enforce that different fields of a struct can be packed / unpacked with different contexts.
