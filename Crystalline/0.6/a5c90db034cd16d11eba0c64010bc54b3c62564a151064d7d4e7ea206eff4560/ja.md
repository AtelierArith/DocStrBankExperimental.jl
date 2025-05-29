```
reduce_ops(ops::AbstractVector{SymOperation{D}},
           cntr::Char,
           conv_or_prim::Bool=true,
           modw::Bool=true) --> Vector{SymOperation{D}}
```

操作 `ops` を削減し、中心 `cntr` に関連する原始基底で同一の操作を削除します。

`conv_or_prim = false` の場合、削減された操作は `cntr` に関連する原始基底で返されます。それ以外の場合は、従来の基底で返されます。`modw = true` の場合、原始基底での比較は単位原始格子ベクトルの剰余で行われます。それ以外の場合は行われません。型 `::Val{P}` の最終引数を指定することで、空間埋め込み次元 `D` とは異なる周期次元 `P` の部分周期群を示すことができます。
