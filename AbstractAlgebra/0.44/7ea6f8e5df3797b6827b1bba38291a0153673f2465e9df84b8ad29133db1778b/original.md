```
ItemQuantity(count::Int, noun::String)
ItemQuantity(count::Int, noun::String, noun_plural::String)
```

A helper object which has the sole purpose of being printed. If `count` is `1` then it is printed as `1 noun`. For any other `count`, the output will be `count noun_plural`. If `noun_plural` is not given, this defaults to `plural(noun)`.

The reason we allow specifying an explicit plural form is that [`plural`](@ref) is not perfect and there may be situations where it does not produce the correct plural form, thus a fallback alternative is prudent to have. Ideally, though, please instead improve `pluralize` to handle your needs correctly.

# Examples

```jldoctest
julia> ItemQuantity(0, "generator")
0 generators

julia> ItemQuantity(1, "generator")
1 generator

julia> ItemQuantity(2, "generator")
2 generators
```

Here is an example with a custom plural form.

```jldoctest
julia> ItemQuantity(0, "ox", "oxen")
0 oxen

julia> ItemQuantity(1, "ox", "oxen")
1 ox

julia> ItemQuantity(2, "ox", "oxen")
2 oxen
```
