```
MeshData(rd::RefElemData, objects, 
         vx::AbstractVector, vy::AbstractVector,
         quadrature_type=Subtriangulation(); 
         quad_rule_face=get_1d_quadrature(rd), 
         precompute_operators=false)
```

モーメントフィッティングを利用したMeshDataのコンストラクタ。正の数値積分重みを保証せず、適応サンプリングを使用して構築するため遅くなります。

!!! 警告: これは将来のバージョンで非推奨または削除される可能性があります。
