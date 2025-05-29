```
dynamic(x)
```

Returns the "dynamic" or non-static form of `x`. If `x` is not a static type, then it is returned unchanged.

`dynamic` ensures that the type of the returned value is always inferred, even if the compiler fails to infer the exact value.

See also: [`known`](@ref)

# Examples

```julia
julia> dynamic(static(1))
1

julia> dynamic(1)
1

```
