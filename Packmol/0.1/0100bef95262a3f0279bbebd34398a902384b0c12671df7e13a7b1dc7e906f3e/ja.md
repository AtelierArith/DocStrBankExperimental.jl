```
pack_monoatomic!(positions::AbstractVector{<:SVector{N,T}}, unitcell, tol)
```

初期位置 `x` と距離許容値 `tol` を持つ単原子系を、周期境界条件を考慮して `unitcell` で定義された単位セルにパックします。

単位セルは、直方体セルの場合はベクトル、三斜晶セルの場合は行列であることができます。

座標と単位セルは二次元または三次元である可能性があります。

# 例

```julia-repl
julia> using Packmol, StaticArrays

julia> coordinates = 100 * rand(SVector{3,Float64}, 10^5);

julia> unitcell = [100.0, 100.0, 100.0]; tolerance = 2.0;

julia> pack_monoatomic!(coordinates, unitcell, tolerance)
```

パッキング後、`coordinates` 配列は重なりのない原子の更新された位置を持つことになります。
