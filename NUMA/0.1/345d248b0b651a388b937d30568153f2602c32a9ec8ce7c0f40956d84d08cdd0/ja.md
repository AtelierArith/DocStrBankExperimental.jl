```julia
numa_node_size(

) -> @NamedTuple{memtot::Int64, memfree::Int64}
numa_node_size(
    node::Integer
) -> @NamedTuple{memtot::Int64, memfree::Int64}

```

指定されたNUMAノードの合計メモリと空きメモリを保持する名前付きタプルを返します。引数としてノードインデックスが提供されていない場合は、`current_numa_node()`が使用されます。
