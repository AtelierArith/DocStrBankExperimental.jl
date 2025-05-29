```
is_real(r::PathResult; tol::Float64 = 1e-6)
```

解が `real` と見なされるのは、解の虚部の無限ノルムが `tol` 以下である場合です。
