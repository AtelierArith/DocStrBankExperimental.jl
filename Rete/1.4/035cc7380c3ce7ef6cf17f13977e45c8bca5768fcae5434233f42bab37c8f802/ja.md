```
askc(continuation, root::AbstractReteRootNode, t::Type)
```

は、`root`でルートされたネットワークに保存されている指定された型のすべての事実に対して`continuation`を呼び出します。

サブタイプは考慮しません。なぜなら、それは同じ事実に対して`continuation`が複数回呼び出されることにつながる可能性があるからです（型自体のメモリノードからとサブタイプのメモリノードから）。

すべてのメモリノードが`root`の直接の出力であると仮定します。

また、`root`のすべての出力が`is_memory_for_type`を実装していると仮定します。
