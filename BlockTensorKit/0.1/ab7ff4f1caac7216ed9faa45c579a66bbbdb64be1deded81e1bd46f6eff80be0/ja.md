```
droptol!(t::AbstractBlockTensorMap, tol=eps(real(scalartype(t)))^(3/4))
```

ノルムが `≤(tol)` のブロックテンソルのエントリを削除します。
