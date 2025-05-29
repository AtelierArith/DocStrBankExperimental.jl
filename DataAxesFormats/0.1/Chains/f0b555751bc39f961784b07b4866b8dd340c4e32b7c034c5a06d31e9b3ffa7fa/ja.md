```
chain_writer(dafs::AbstractVector{<:DafReader}; name::Maybe{AbstractString} = nothing)::DafWriter
```

チェーンの [`DafReader`](@ref) データのチェーンラッパーを作成し、それらを単一の [`DafWriter`](@ref) として提示します。これは [`chain_reader`](@ref) に似ていますが、チェーンの最後のエントリが [`DafWriter`](@ref) である必要があります。チェーンへの変更や追加は、この最終的なライターのみに向けられます。

!!! note
    削除は、最終的なライターにのみ存在するデータに対してのみ許可されます。つまり、チェーン内の何かを削除することは、いずれかのリーダーに存在するものからは不可能であり、上書きすることのみが可能です。

