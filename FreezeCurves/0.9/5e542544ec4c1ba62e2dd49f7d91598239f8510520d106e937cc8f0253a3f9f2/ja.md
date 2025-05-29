```
sfccsolve(obj::AbstractSFCCObjective, solver::SFCCSolver, x₀, ::Val{return_all}=Val{true}()) where {return_all}
```

与えられた目的 `obj` を `solver` と初期推定 `x₀` を使用して解きます。`return_all=true` の場合、`sfccsolve` は少なくとも温度解 `T`、液体水分含量 `θw`、比熱容量 `C`、および定義された液体水分含量の導関数 `∂θw∂T` を含む名前付きタプルを返す必要があります。ソルバー固有の追加値も含めることができます。
