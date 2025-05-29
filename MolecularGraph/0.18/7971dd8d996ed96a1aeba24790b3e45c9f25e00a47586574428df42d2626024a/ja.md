```
edge_substruct_matches(mol1, mol2; kwargs...) -> Iterator
```

`mol`が`query`を部分構造として持つ場合、`mol`と`query`の間のノードマッピングを生成する遅延イテレータを返します。利用可能なオプションについては、[`substruct_matches`](@ref)を参照してください。
