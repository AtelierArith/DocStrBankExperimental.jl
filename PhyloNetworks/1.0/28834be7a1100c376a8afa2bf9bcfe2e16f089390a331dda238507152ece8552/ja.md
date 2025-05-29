```
cladewiseorder!(net::HybridNetwork)
```

内部属性 `net.vec_int1` を更新します。ネットワークのプロットに使用されます。主要な系統樹では、特定のクレード内のすべてのノードが連続しています。この関数は、ツリー上でノードの前順序も提供します。エッジの方向は、[`cladewiseorder!`](@ref) を呼び出す前に正しくする必要があります。[`directedges!`](@ref) を使用してください。
