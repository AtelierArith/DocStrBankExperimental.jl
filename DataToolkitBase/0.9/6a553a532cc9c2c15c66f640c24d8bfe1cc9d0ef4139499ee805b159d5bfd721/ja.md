```
loadcollection!(source::Union{<:AbstractString, <:IO}, mod::Module=Base.Main;
                soft::Bool=false, index::Int=1)
```

`source` からデータコレクションをロードし、`index` にデータスタックに追加します。`source` は `read(source, DataCollection)` によって受け入れられる必要があります。

`mod` は `loadcollection!` が呼び出されているモジュールに設定する必要があります。これは、コレクションによってコードが実行されるときに重要です。そのため、通常は次のように呼び出すのが適切です：

```julia
loadcollection!(source, @__MODULE__; soft)
```

`soft` が設定されている場合、同じ UUID を持つデータコレクションがすでに存在する場合は、何も行われず、`nothing` が返されます。
