```
@patch expr
```

Creates a patch from a function definition. A patch can be used with [`apply`](@ref) to temporarily include the patch when performing multiple dispatch on `@mock`ed call sites.

See also: [`@mock`](@ref), [`apply`](@ref).
