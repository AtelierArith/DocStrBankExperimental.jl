```
static(x)
```

Returns a static form of `x`. If `x` is already in a static form then `x` is returned. If there is no static alternative for `x` then an error is thrown.

See also: [`is_static`](@ref), [`known`](@ref)

# Examples

```julia
julia> using Static

julia> static(1)
static(1)

julia> static(true)
True()

julia> static(:x)
static(:x)

```
