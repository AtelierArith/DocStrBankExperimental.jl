```
@bitflagx [T=FlagTypeName] BitFlagName[::BaseType] value1[=x] value2[=y]
```

Like [`@bitflag`](@ref) but instead scopes the new type `FlagTypeName` (named `T` if not overridden via the first optional argument) and member constants within a module named `BitFlagName`.

# Examples

```jldoctest scopedflags julia> @bitflagx ScopedItems apple=1 fork=2 napkin=4

julia> f(x::ScopedItems.T) = "I'm a scoped flag with value: :x" f (generic function with 1 method

julia> f(ScopedItems.apple | ScopedItems.fork) "I'm a scoped flag with value: (fork | apple)"
