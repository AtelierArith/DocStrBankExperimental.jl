```
setnnbonds(lat, args...; overwrite=false)
```

最近接隣接結合 `args` を格子 `lat` に追加します。`overwrite` が `true` の場合、デフォルトの最近接隣接結合は `args` に置き換えられます。そうでない場合、新しい結合はデフォルトとマージされます。

各 `args` は結合タイプまたは距離-結合ペアであることができます。

## 例

```jldoctest
julia> using LatticeModels

julia> lat = SquareLattice(3, 3);

julia> lat2 = setnnbonds(lat, SiteDistance(0 .. 1), SiteDistance(1 .. 2));

julia> lat2.nnbonds
最近接隣接ホッピング:
  #1 =>
    SiteDistance(0 .. 1)
  #2 =>
    SiteDistance(1 .. 2)
```
