```
ルックアップ
```

[`Lookup`](@ref) と [`Selector`](@ref) のためのモジュール、DimensionalData.jl で使用されます。

`Lookup` は、[`Selector`](@ref) でインデックス付けされたときにルックアップインデックスに特定の動作を与える特性と `AbstractArray` ラッパーを定義します。

例えば、これにより配列の順序を追跡できるため、配列が逆になっても高速なインデックス付けが機能します。

`Lookup` タイプとメソッドをスコープに読み込むには：

```julia
using DimensionalData
using DimensionalData.Lookups
```
