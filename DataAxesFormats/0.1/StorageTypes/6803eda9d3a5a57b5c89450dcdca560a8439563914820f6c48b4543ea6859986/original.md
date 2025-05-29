```
StorageScalar = Union{StorageReal, <:AbstractString}
```

Types that can be used as scalars, or elements in stored matrices or vectors.

This is restricted to [`StorageReal`](@ref) (including Booleans) and strings. It is arguably too restrictive, as in principle we could support any arbitrary `isbitstype`. However, in practice this would cause much trouble when accessing the data from other systems (specifically Python and R). Since `Daf` targets storing scientific data (especially biological data), as opposed to "anything at all", this restriction seems reasonable.
