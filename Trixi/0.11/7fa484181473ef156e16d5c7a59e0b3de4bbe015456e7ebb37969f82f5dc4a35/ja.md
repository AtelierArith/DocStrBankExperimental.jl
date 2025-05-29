```
adapt_to_mesh_level(u_ode, semi, level)
adapt_to_mesh_level(sol::Trixi.TrixiODESolution, level)
```

通常の適応メッシュ細分化ルーチンを使用して、半離散化 `semi` を用いて解 `u_ode` を適応的に細分化/粗視化し、細分化レベル `level` の均一に細分化されたグリッドに向けます。解と半離散化はコピーされるため、元のオブジェクトは*変更されません*。

便利なメソッドはODE解オブジェクトを受け入れ、必要に応じて解と半離散化を抽出します。

参照: [`adapt_to_mesh_level!`](@ref)
