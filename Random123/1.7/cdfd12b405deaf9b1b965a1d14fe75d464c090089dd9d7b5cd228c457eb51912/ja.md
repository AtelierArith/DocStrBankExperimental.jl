```
philox(key::NTuple{1,T}, ctr::NTuple{2,T}, ::Val{R})::NTuple{2,T}
philox(key::NTuple{2,T}, ctr::NTuple{4,T}, ::Val{R})::NTuple{4,T}
```

[`Philox2x`](@ref) と [`Philox4x`](@ref) の関数型バリアント。入力から `T = UInt64` または `T = UInt32` 型の擬似乱数出力を生成します。この関数は可変性や副作用がありません。
