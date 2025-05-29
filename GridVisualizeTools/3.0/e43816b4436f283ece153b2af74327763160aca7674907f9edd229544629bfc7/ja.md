```julia
extract_visible_cells3D(
    coord,
    cellnodes,
    cellregions,
    nregions,
    xyzcut;
    primepoints,
    Tp,
    Tf
)

```

可視テトラヘドラを抽出します - それは `x=xyzcut[1]` または `y=xyzcut[2]` または `z=xyzcut[3]` の平面と交差します。

メッシュ（Makie, MeshCat）または三角面（pyplot）として描画するために、各領域に対応する点とファセットを返します。
