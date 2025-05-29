```
write_dataset(parent::Union{File,Group}, name::Union{AbstractString,Nothing}, data; pv...)
```

`data`を使用してデータセットを作成および書き込みます。キーワードは[`create_dataset`](@ref)に転送されます。名前として`nothing`を指定すると、匿名データセットが作成されます。

関連情報として[`create_dataset`](@ref)を参照してください。
