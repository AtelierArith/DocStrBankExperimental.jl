```
globalindices(A::BlockHaloArray, block_index, local_indices) -> global_indices
```

ブロックインデックスとローカル座標を指定すると、グローバルインデックスを返します。

# 例

```
julia> globalindices(A, 2, (3, 4)) -> (8, 10)
```
