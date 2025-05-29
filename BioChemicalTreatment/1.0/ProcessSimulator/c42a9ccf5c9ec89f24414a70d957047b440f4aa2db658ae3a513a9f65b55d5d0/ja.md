```
exogenous_outputs(sys, idxs::Union{Int, Vector{Int}})
```

`sys`のインデックス`idxs`にある外生出力コネクタを取得します。

`idxs`が単一の整数の場合、出力はコネクタになります。整数のベクトルの場合、出力はコネクタのベクトルになります。
