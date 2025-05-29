```
make_compute_exp_tendency(model::PlantHydraulicsModel, _)
```

PlantHydraulicsModelのcompute*exp*tendency!関数を作成する関数です。compute*exp*tendency!関数は、SciMLBase.jlのrhs関数に準拠している必要があります。

以下で、`fa`は関連する断面積（単位面積あたりの地面、または面積インデックス、AI）で乗算されたフラックスを示します。i番目のコンパートメントの傾向は次のように書くことができます：∂ϑ[i]/∂t = 1/(AI*dz)[fa[i]-fa[i+1])。

植物が存在しないためにarea_indexがゼロの場合、AIdzはゼロになり、分子に現れるフラックス`fa`はAIでスケーリングされるためゼロになります。

ゼロで割るのを防ぐために、"AI/(AI x dz)"を"AI/max(AI x dz, eps(FT))"に変更します。
