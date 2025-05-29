```
cyclicshift(v::AbstractVector, nrow)
```

`v`の各列が`v`の後に`v`の循環シフトが続く、サイズ`nrow` x `length(v)`の`eltype(v)`行列を返します。

```@example
cyclicshift('a':'d', 8)
```
