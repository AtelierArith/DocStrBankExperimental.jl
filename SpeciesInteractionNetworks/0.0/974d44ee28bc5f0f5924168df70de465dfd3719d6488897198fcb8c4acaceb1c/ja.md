```
SpeciesInteractionNetwork{P<:Partiteness, E<:Interactions}
```

`SpeciesInteractionNetwork`型は、種の相互作用ネットワークを表します。

この型には2つのフィールドがあります：`nodes`（`Partiteness`）と`edges`（`Interactions`）。これら2つの型はパラメトリックであるため、ネットワーク内のデータ構造について知っているすべてのことを型だけを見て学ぶことができます。

例えば、種がシンボルで相互作用が32ビット浮動小数点数である二部量的ネットワークは、次の型を持ちます。

```
SpeciesInteractionNetwork{Bipartite{Symbol}, Interactions{Float32}}
```

これにより、パッケージ全体で非常に専門的なディスパッチとインデックス付けが可能になります。
