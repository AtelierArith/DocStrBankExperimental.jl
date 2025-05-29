```
syncarray!(v::CeedVector, mtype::MemType)
```

指定された[`MemType`](@ref)に[`CeedVector`](@ref)を同期します。この関数は、[`setarray!`](@ref)で設定された配列の同期を強制するために使用されます。要求されたメモリタイプがすでに同期されている場合、この関数は何もしません。
