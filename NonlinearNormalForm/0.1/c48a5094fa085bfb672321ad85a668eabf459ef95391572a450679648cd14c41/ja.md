```
NonlinearNormalForm.DAMap(m::Union{TaylorMap{S,T,U,V,W},Probe{S,T,U,V,W}}; use::UseType=m, idpt::Union{Nothing,Bool}=m.idpt) where {S,T,U,V,W}
```

渡された `TaylorMap` の新しいコピーを `NonlinearNormalForm.DAMap` として作成します。

`use` が指定されていない場合、`m` と同じ GTPSA `Descriptor` が使用されます。`use` が指定されている場合（別の `Descriptor`、`TaylorMap`、または `TPS` を含む `Probe` である可能性があります）、新しい `NonlinearNormalForm.DAMap` としての `m` のコピーは `use` にあるのと同じ `Descriptor` を持ちます。ただし、変数 + パラメータの総数は一致する必要がありますが、次数は異なっていても構いません。

`idpt` が指定されていない場合、`m` と同じ `idpt` が使用されます。そうでない場合は、指定されたものが使用されます。
