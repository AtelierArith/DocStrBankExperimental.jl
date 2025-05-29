```
Reflect
```

Placeholder type for reflected type string.

# Type Alias

if the corresponding type has a [`type_alias`](@ref) defined, serialization and parsing will use the [`type_alias`](@ref) instead of the type name, this only works on concrete types since the alias cannot contain any type var information.

# Example

the following option struct

```julia
@option struct MyOption
    type::Reflect
    name::String = "Sam"
end
```

would be equivalent to

```toml
type = "MyOption"
name = "Sam"
```

this is useful for defining list of different types etc.
