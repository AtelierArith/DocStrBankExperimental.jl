```
count_chains(causet, chain_length) -> Int64
```

`causet`内の長さ`chain_length`の原子を持つ厳密に昇順の順序付けられたチェーンの数をカウントします。`chain_length = 2`の場合、これは[`count_relations`](@ref)に相当します。
