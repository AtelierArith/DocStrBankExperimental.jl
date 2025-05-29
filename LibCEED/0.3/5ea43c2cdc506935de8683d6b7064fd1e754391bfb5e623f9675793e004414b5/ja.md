```
getmultiplicity(r::ElemRestriction)
```

[`ElemRestriction`](@ref) のノードの重複度を取得するための便利な関数で、結果は新しく割り当てられた Julia `Vector{CeedScalar}` に返されます（[`getmultiplicity!`](@ref) も参照）。
