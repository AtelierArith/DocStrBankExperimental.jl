```
NonlinearNormalForm.TPSAMap(m::Union{TaylorMap{S,T,U,V,W},Probe{S,T,U,V,W}}; use::UseType=m, idpt::Union{Nothing,Bool}=m.idpt) where {S,T,U,V,W}
```

渡された `TaylorMap` の新しいコピーを `NonlinearNormalForm.TPSAMap` として作成します。

`use` が指定されていない場合、`m` と同じ GTPSA `Descriptor` が使用されます。`use` が指定されている場合（別の `Descriptor`、`TaylorMap`、または `TPS` を含む `Probe` である可能性があります）、`m` のコピーは新しい `NonlinearNormalForm.TPSAMap` として `use` の `Descriptor` と同じになります。ただし、変数の総数 + パラメータは一致する必要がありますが、次数は異なっていても構いません。

`idpt` が指定されていない場合、`m` と同じ `idpt` が使用されます。そうでない場合は、指定されたものが使用されます。
