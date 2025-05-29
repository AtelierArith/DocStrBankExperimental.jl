```julia
abstract type NodePermutation <: ExtendableGrids.AbstractGridIntegerArray1D
```

ノードの順列を表すキータイプで、分割されたグリッドが未分割の原点に対してどのように配置されているかを示します。

`pgrid` が分割されたグリッドで、`grid` が未分割の原点である場合、次のようになります。

`pgrid[Coordinates][:,pgrid[NodePermutation]]==grid[Coordinates]`
