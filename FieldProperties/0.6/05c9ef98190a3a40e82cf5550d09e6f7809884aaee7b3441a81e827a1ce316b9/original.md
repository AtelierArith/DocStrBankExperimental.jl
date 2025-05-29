```
description(x) -> String
```

Description that may say whatever you like.

---

```
description(x::AbstractProperty) -> String
```

Returns description for property `x`.

## Examples

```jldoctest
julia> using FieldProperties

julia> description(description)
"Description that may say whatever you like.\n"
```
