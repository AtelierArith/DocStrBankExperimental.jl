```
AbstractMesh
```

[`PB.Domain`](@ref) のための追加の幾何学的およびトポロジー情報を定義します。

具体的なサブタイプは、以下のメソッドを実装する必要があります：

[`available_spaces`](@ref) サポートされている [`PB.AbstractSpace`](@ref) タイプのタプル。

[`PB.has_internal_cartesian`](@ref) サブタイプが外部（直交）表現とは異なる内部空間表現を使用している場合は `true`。

[`PB.get_dimensions`](@ref)

[`PB.internal_size`](@ref)、オプションで [`PB.cartesian_size`](@ref)

[`PB.Grids.set_subdomain!`](@ref)、[`PB.Grids.get_subdomain`](@ref)

[`PB.Grids.create_default_cellrange`](@ref)

# 内部および直交表現

サブタイプが外部（直交）表現とは異なる内部表現を使用している場合は、[`PB.has_internal_cartesian`](@ref) を `true` に設定し、[`cartesian_to_internal`](@ref)、[`internal_to_cartesian`](@ref)、および [`PB.cartesian_size`](@ref) を実装する必要があります。
