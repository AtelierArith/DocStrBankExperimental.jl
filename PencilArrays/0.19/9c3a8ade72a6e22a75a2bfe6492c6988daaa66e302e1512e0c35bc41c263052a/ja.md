```
PencilArrayCollection
```

`UnionAll` 型は [`PencilArray`](@ref) のコレクションを表します。

このコレクションは、`PencilArray` のタプルまたは配列である可能性があります。

コレクションは **仮定として** 同種であり、各配列は同じ特性を持ち、特に同じ [`Pencil`](@ref) 構成に関連付けられています。

便利のために、`PencilArray` に対して定義されている特定の操作は、`PencilArrayCollection` に対しても定義されており、単一の `PencilArray` に対しての値と同じ値を返します。いくつかの例としては、[`pencil`](@ref)、[`range_local`](@ref)、および [`get_comm`](@ref) があります。

また、`size`、`ndims`、`eltype` などの `Base` の関数は、タプルや配列に対してすでに定義があるため、`PencilArrayCollection` に対して **オーバーロード** されていないことに注意してください（再定義すると型の略奪になります...）。
