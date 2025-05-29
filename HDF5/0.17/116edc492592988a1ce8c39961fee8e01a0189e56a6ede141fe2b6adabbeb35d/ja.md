```
open_group(parent::Union{File,Group}, path::AbstractString; properties...)
```

`parent`オブジェクトの`path`にある既存の[`Group`](@ref)を開きます。

オプションのキーワード引数には、[`GroupAccessProperties`](@ref)に属する任意のキーワードが含まれます。
