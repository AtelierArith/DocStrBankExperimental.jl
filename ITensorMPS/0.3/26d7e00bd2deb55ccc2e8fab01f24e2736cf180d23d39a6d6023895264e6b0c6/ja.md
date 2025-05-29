```
siteinds(M::Union{MPS, MPO}}, j::Integer; kwargs...)
```

サイト `j` におけるMPOまたはMPSのサイトインデックスをIndexSetとして返します。

オプションで、`plev`や`tags`のようなキーワード引数を使用して、プライムタグやプライムレベルをフィルタリングできます。
