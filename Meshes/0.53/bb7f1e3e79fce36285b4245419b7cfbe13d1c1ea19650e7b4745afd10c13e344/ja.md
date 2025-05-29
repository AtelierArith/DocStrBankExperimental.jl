```
SimpleMesh(vertices, topology)
```

`vertices` と `topology` を持つシンプルなメッシュ。

```
SimpleMesh(vertices, connectivities; relations=false)
```

代わりに、`vertices` と `connectivities` を持つシンプルなメッシュを構築します。オプション `relations` は、`connectivities` がメッシュの要素を表すと仮定して、トポロジー関係を構築するために使用できます。

## 例

```julia
julia> points = [(0.0, 0.0),(1.0, 0.0), (1.0, 1.0)]
julia> connec = [connect((1,2,3))]
julia> mesh   = SimpleMesh(points, connec)
```

他にも [`Topology`](@ref)、[`GridTopology`](@ref)、[`HalfEdgeTopology`](@ref)、[`SimpleTopology`](@ref) を参照してください。

### 注意事項

オプション `relations=true` は、メッシュの基礎となるトポロジーを [`SimpleTopology`](@ref) の代わりに [`HalfEdgeTopology`](@ref) に変更します。
