```
reorder!(tree::T, treeda::D) where {T <: iTree, D <: iTree}
```

ツリーに従って、ティップの数に基づいて両方のツリーの娘の枝の順序を再配置します。娘1は常に娘2よりも多くなります。
