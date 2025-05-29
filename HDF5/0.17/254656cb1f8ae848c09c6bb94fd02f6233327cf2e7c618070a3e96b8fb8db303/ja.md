```
create_group(parent::Union{File,Group}, path::AbstractString; properties...)
```

`parent`オブジェクトの`path`に新しい[`Group`](@ref)を作成します。オプションのキーワード引数には、[`LinkCreateProperties`](@ref)または[`GroupCreateProperties`](@ref)に属する任意のキーワードが含まれます。
