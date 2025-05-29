```
description_list(ps...) -> String
```

Returns a markdown list where eache element of `ps` is formatted as:

```
* name(ps[i]): description(ps[i]).
```

## Examples

```jldoctest
julia> using FieldProperties

julia> description_list(description, calmax)
"* `description`: Description that may say whatever you like.\n* `calmax`: Specifies maximum element for display purposes. If not specified returns the maximum value in the collection.\n"
```
