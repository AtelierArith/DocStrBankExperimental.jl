```julia
extract_visible_bfaces3D(
    coord,
    bfacenodes,
    bfaceregions,
    nbregions,
    xyzcut;
    primepoints,
    Tp,
    Tf
)

```

可視境界面を抽出します - 平面 `x=xyzcut[1]` または `y=xyzcut[2]` または `z=xyzcut[3]` によって切断されていないもの。

メッシュ（Makie, MeshCat）または三角面（pyplot）として描画するために、各領域に対応する点とファセットを返します。
