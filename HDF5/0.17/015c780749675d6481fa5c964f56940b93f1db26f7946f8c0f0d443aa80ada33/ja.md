```
open_datatype(parent::Union{File,Group}, path::AbstractString; properties...)
```

`parent`オブジェクトの`path`にある既存の[`Datatype`](@ref)を開きます。

オプションのキーワード引数には、[`DatatypeAccessProperties`](@ref)に属する任意のキーワードが含まれます。
