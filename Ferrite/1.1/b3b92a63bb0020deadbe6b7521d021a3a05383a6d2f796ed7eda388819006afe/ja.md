```
reinit!(
    iv::InterfaceValues,
    cell_here::AbstractCell, coords_here::AbstractVector{Vec{dim, T}}, facet_here::Int,
    cell_there::AbstractCell, coords_there::AbstractVector{Vec{dim, T}}, facet_there::Int
)
```

`cell_here`（セル座標 `coords_here` を持つ）と `cell_there`（セル座標 `coords_there` を持つ）との間のインターフェースの [`InterfaceValues`](@ref) を更新します。`facet_here` と `facet_there` は、それぞれのセルの（ローカル）ファセット番号です。
