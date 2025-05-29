```
chain_cardinality_of(causet, chain[, max_cardinality]) -> Union{NTuple, Nothing}
```

`chain`のチェーンのカーディナリティを計算します。`chain`がチェーンでない場合や、`chain`内の原子が因果的に順序付けられていない場合は`nothing`を返します。
