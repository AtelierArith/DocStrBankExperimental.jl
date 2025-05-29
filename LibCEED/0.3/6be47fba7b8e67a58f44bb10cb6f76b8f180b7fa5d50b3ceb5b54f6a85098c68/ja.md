```
getmultiplicity!(r::ElemRestriction, v::AbstractCeedVector)
```

[`ElemRestriction`](@ref)内のノードの重複度を取得します。[`CeedVector`](@ref) `v`はLベクトルである必要があります（すなわち、`length(v) == getlvectorsize(r)`、詳細は[`create_lvector`](@ref)を参照）。
