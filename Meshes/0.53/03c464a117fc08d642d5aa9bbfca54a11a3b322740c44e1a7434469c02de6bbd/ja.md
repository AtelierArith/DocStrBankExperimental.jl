```
topoconvert(T, mesh)
```

`mesh`の基盤となるトポロジーをタイプ`T`のトポロジーに変換します。

## 例

効率的なトポロジー関係のために基盤となるトポロジーを[`HalfEdgeTopology`](@ref)に変換します。

```julia
newmesh = topoconvert(HalfEdgeTopology, mesh)
```
