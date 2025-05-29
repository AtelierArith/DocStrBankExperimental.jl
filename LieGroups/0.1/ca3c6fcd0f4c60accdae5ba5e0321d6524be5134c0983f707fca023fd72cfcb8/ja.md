```
PowerLieGroup(G::LieGroup, args...; kwargs...)
(G::LieGroup)^(n::Integer) = PowerLieGroup(G, n)
```

`G`の`n`乗のLie群または多様体`M`の[`LieGroup`](@ref)を生成します。Lie群`G`が渡された場合、[`PowerLieGroup`](@ref)上の群演算は`G`上のものと同じですが、要素ごとに適用されます。内部的には、対応する[`PowerGroupOperation`](@ref)が作成されます。多様体`M`を渡す場合は、対応する[`PowerGroupOperation`](@ref)を自分で提供する必要があります。

引数`args...`およびキーワード引数`kwargs...`は、[`PowerManifold`](@extref `ManifoldsBase.PowerManifold`)のコンストラクタに渡されます。これには特に多様体の`size`が含まれ、[`NestedPowerRepresentation`](@extref `ManifoldsBase.NestedPowerRepresentation`)を指定することができます。
