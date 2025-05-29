```
Axis(axis::AbstractString) <: QueryOperation
```

結果軸を指定するためのクエリ操作です。文字列 [`Query`](@ref) では、`/` 演算子の後に軸名を続けて指定します。

これは、ベクトルクエリ（例：`/ cell : batch`）の場合は少なくとも1回、行列の場合は2回指定する必要があります（例：`/ cell / gene : UMIs`）。軸は、[`And`](@ref)、[`AndNot`](@ref)、[`Or`](@ref)、[`OrNot`](@ref)、[`Xor`](@ref)、および [`XorNot`](@ref) を使用してブールマスクでフィルタリングできます（例：`/ gene & is_marker : is_noisy`）。あるいは、[`IsEqual`](@ref) を使用して軸から単一のエントリを選択することもできます（例：`/ gene = FOX1 : is_noisy`、`/ cell / gene = FOX1 : UMIs`、`/ cell = C1 / gene = FOX1 : UMIs`）。最後に、[`ReductionOperation`](@ref) を使用して行列をベクトルに、ベクトルをスカラーに縮小することができます（例：`/ gene / cell : UMIs %> Sum %> Mean`）。

!!! note
    これ、[`Names`](@ref) および [`Lookup`](@ref) は、完全な [`Query`](@ref) としても機能する唯一の [`QueryOperation`](@ref) です。

