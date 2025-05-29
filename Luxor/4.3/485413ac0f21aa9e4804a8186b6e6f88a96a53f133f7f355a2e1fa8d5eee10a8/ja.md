```
add_mesh_patch(pattern::Mesh, plist::Array{Point}, colors=Vector{Colors.Colorant})
```

`pattern`のメッシュパターンに新しいパッチを追加します。

提供された`points`ポリゴンの最初の三つまたは四つの辺がメッシュ形状の三つまたは四つの辺を定義します。

`colors`配列は各コーナーポイントの色を定義します。必要に応じて色は再利用されます。少なくとも一つの色を提供する必要があります。
