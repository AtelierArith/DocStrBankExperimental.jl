```
addroute!(p, m::OpenStreetMapX.MapData,
               route::Vector{OpenStreetMapX.LLA};
               route_color::Union{String, Plots.RGB} ="0x000053",
               km::Bool=false,
               start_name="A", end_name="B",
               fontsize=15
               )
```

地図 `m` を表すプロット `p` に LLA 座標の `route` を追加します。

ルート座標 `route` のリストの最初の要素は `start_name` で注釈され、最後の要素は `end_name` で注釈されます。`km` パラメータを使用すると、メートルの代わりに地図のキロメートルスケールを持つことができます。

さらなるプロットの更新に使用できるオブジェクトを返します。
