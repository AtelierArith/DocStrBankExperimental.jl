```
names(x::Module; all::Bool = false, imported::Bool = false)
```

Get an array of the names exported by a `Module`, excluding deprecated names. If `all` is true, then the list also includes non-exported names defined in the module, deprecated names, and compiler-generated names. If `imported` is true, then names explicitly imported from other modules are also included.

As a special case, all names defined in `Main` are considered "exported", since it is not idiomatic to explicitly export names from `Main`.

See also: [`@locals`](@ref Base.@locals), [`@__MODULE__`](@ref).
