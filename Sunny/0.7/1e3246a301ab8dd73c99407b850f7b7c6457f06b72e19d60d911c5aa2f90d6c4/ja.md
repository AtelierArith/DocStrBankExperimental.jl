```
set_pair_coupling_at!(sys::System, op, site1::Site, site2::Site; offset=nothing)
```

2つの[`Site`](@ref)を接続する単一の結合に沿った任意の結合を設定し、結晶対称性を無視します。この結合に対する以前の結合は上書きされます。システムは[`to_inhomogeneous`](@ref)を介して不均一な相互作用をサポートする必要があります。

[`symmetry_equivalent_bonds`](@ref)を使用して、均一なシステムにおける特定の[`Bond`](@ref)に対して対称的に等しい`(site1, site2, offset)`の値を見つけます。小さなシステムでは、`offset`ベクトル（単位セルの倍数で）は周期的なラッピングのあいまいさを解消します。

演算子`op`は、2つのスピンダイポール演算子を受け入れる匿名関数として提供することも、2つのサイトのテンソル積空間で作用する行列として提供することもできます。[`set_pair_coupling!`](@ref)のドキュメントには、`op`を構築する例が示されています。 ```
