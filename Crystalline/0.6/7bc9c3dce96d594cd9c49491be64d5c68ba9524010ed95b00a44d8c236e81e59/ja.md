```julia
sitegroups(sg::Crystalline.SpaceGroup{D}) -> Any

```

空間群に関連付けられたすべてのサイト対称群を返します。これは、`sg :: SpaceGroup{D}`として指定するか、従来の番号`sgnum`と次元`D`で指定します（省略した場合、`D`はデフォルトで3になります）。

特定のワイコフ位置のサイト対称群の計算については、[`sitegroup`](@ref)も参照してください。
