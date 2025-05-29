```
triangulate(surf::ParametricSurface{S,N}, quads_per_row::Int, extensionu::Bool = false, extensionv::Bool = false, radialu::Bool = false, radialv::Bool = false)
```

パラメトリックサーフェスを表す三角形の配列を作成します。頂点はUV空間の均等なグリッドでサンプリングされます。サーフェスはuおよびvをそれぞれ1%拡張することができ、uまたはvのいずれかを放射状として指定すると、サーフェス上の半径（例えば、ゼルニケのrho）を決定し、その次元が平方根を使用してサンプリングされるため、三角形の面積が均一になります。この場合、拡張は最大値にのみ適用されます。
