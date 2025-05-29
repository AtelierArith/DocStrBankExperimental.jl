```
surfacepotential(points,normals,topology,μ,ψ0::Function)
```

与えられた形状に対する表面場を返します。この形状は、`points`、`normals`、および `topology` で定義された三角メッシュによって定義され、∇ψ が μ で特徴付けられた法線方向にジャンプを持つ境界条件に対して、外部自由場はポテンシャル ψ0 によって与えられます。
