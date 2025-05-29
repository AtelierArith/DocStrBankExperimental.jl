```
@bitflag BitFlagName[::BaseType] value1[=x] value2[=y]
```

Create a `BitFlag{BaseType}` subtype with name `BitFlagName` and flag member values of `value1` and `value2` with optional assigned values of `x` and `y`, respectively. `BitFlagName` can be used just like other types and flag member values as regular values, such as

# Examples

```jldoctest itemflags
julia> @bitflag Items apple=1 fork=2 napkin=4

julia> f(x::Items) = "I'm a flag with value: $x"
f (generic function with 1 method)

julia> f(apple)
"I'm a flag with value: apple"

julia> f(apple | fork)
"I'm a flag with value: (apple | fork)"
```

Values can also be specified inside a `begin` block, e.g.

```julia
@bitflag BitFlagName begin
    value1
    value2
end
```

`BaseType`, which defaults to [`UInt32`](@ref), must be a primitive subtype of `Unsigned`. Member values can be converted between the bit flag type and `BaseType`. `read` and `write` perform these conversions automatically. In case the bitflag is created with a non-default `BaseType`, `Integer(value1)` will return the integer `value1` with the type `BaseType`.

To list all the instances of an bitflag use `instances`, e.g.

```jldoctest itemflags
julia> instances(Items)
(apple::Items = 0x00000001, fork::Items = 0x00000002, napkin::Items = 0x00000004)
```
