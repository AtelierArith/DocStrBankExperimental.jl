```
setarray!(v::CeedVector, mtype::MemType, cmode::CopyMode, arr)
```

[`CeedVector`](@ref)によって使用される配列を設定し、適用可能な場合は以前に割り当てられた配列を解放します。バックエンドは、異なる[`MemType`](@ref)に値をコピーする場合があります。[`syncarray!`](@ref)および[`takearray!`](@ref)も参照してください。

!!! warning "OWN_POINTER CopyModeを避ける"
    [`CopyMode`](@ref) `OWN_POINTER`は、Juliaによって割り当てられた配列には適していません。なぜなら、それらはlibCEEDから適切に解放することができないからです。

