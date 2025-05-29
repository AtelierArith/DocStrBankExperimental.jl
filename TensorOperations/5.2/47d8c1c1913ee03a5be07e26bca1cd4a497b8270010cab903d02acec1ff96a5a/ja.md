```
tensoralloc(ttype, structure, [istemp=false, allocator])
```

タイプ `ttype` と構造 `structure` のテンソルのためにメモリを割り当てます。オプションの第三引数は、結果が一時的なテンソルとして使用されることを示すために使用でき、場合によっては一部のアロケータ（オプションの第四引数）で異なる割り当て戦略が使用されることがあります。

他にも [`tensoralloc_add`](@ref)、[`tensoralloc_contract`](@ref)、および [`tensorfree!`](@ref) を参照してください。
