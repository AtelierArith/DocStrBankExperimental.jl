```
@se EnumName[::BaseType] value1[=x] value2[=y]
@se EnumName[::BaseType] value1[=>string1] value2[=>string2]
```

Create an `Enum{BaseType}` subtype with name `EnumName` and enum member values of `value1` and `value2` with optional assigned values of `x` and `y`, respectively, or with `type=>description` pairs. `EnumName` will be defined as `EnumName.EnumNameEnum`, where `EnumName` is a module, and `EnumNameEnum` is the type.  This type can be used just like other types and enum member values as regular values.

# Examples

```jldoctest fruitenum
julia> @se Fruit apple=1 orange=2 kiwi=3
julia> f(x::Fruit) = "I'm a Fruit with value: $(Int(x))"
f (generic function with 1 method)
julia> f(apple)
"I'm a Fruit with value: 1"
julia> Fruit(1)
apple::Fruit = 1
julia> SuperEnum.@se Lang zh=>"中文" en=>"English" ja=>"日本语"
WARNING: replacing module Lang.
Main.Lang
julia> string(Lang.zh)
"中文"
julia> string(Lang.en)
"English"
julia> string(Lang.ja)
"日本语"
julia> Lang.LangEnum
Enum Main.Lang.LangEnum:
zh = 0
en = 1
ja = 2
```

Values can also be specified inside a `begin` block, e.g.

```julia
@se EnumName begin
    value1
    value2
end
```

`BaseType`, which defaults to [`Int32`](@ref), must be a primitive subtype of `Integer`. Member values can be converted between the enum type and `BaseType`. `read` and `write` perform these conversions automatically. To list all the instances of an enum use `instances`, e.g.

```jldoctest fruitenum
julia> instances(Fruit)
(apple, orange, kiwi)
```
