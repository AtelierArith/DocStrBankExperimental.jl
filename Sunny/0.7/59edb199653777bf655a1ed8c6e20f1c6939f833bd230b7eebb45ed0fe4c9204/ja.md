```
resize_supercell(sys::System, dims::NTuple{3, Int})
```

指定された数の従来の単位セルを各格子ベクトル方向に持つ[`System`](@ref)を作成します。相互作用、スピン、およびその他の設定は`sys`から継承されます。

次のように同等です：

```julia
reshape_supercell(sys, [dims[1] 0 0; 0 dims[2] 0; 0 0 dims[3]])
```

他にも[`reshape_supercell`](@ref)や[`repeat_periodically`](@ref)を参照してください。
