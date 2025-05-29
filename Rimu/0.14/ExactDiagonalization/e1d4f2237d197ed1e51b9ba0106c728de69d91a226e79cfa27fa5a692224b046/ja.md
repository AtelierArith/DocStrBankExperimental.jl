```
build_basis(addr::AbstractFockAddress)
build_basis(::Type{<:AbstractFockAddress}) -> basis
```

与えられたタイプのすべての可能なフォック状態をベクターとして返します。このメソッドは `build_basis(::AbstractHamiltonian, ...)` よりも *はるかに* 高速ですが、行列のブロッキングは考慮していません。このバージョンの `build_basis` は追加の引数を受け付けません。

[`OccupationNumberFS`](@ref Main.Rimu.OccupationNumberFS) 以外のすべてのアドレスタイプがサポートされています。

`addr` の [`dimension`](@ref) と等しい長さのソートされたベクターを返します。

また、[`AbstractFockAddress`](@ref) も参照してください。
