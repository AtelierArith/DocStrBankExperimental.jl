```
emit(node, fact)
```

Distribute's `fact` to each of `node`'s outputs by calling [`receive`](@ref) on the output node and `fact`.
