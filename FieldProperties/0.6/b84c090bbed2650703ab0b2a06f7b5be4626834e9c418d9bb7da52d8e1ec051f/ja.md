```
description_list(ps...) -> String
```

`ps`の各要素が次のようにフォーマットされたマークダウンリストを返します:

```
* name(ps[i]): description(ps[i]).
```

## 例

```jldoctest
julia> using FieldProperties

julia> description_list(description, calmax)
"* `description`: Description that may say whatever you like.\n* `calmax`: Specifies maximum element for display purposes. If not specified returns the maximum value in the collection.\n"
```
