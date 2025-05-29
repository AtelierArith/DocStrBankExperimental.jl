```
plan_route!(agent, dest, model::ABM{<:OpenStreetMapSpace};
            return_trip = false, kwargs...) → success
```

`agent`の現在位置から`dest`で指定された場所（交差点または道路上のポイント）までのルートを計画します。既存のルートは上書きされます。

`return_trip = true`の場合、スタート ⟶ フィニッシュ ⟶ スタートのルートが計画されます。他のすべてのキーワードは[`LightOSM.shortest_path`](https://deloittedigitalapac.github.io/LightOSM.jl/docs/shortest_path/#LightOSM.shortest_path)に渡されます。

`dest`へのパスが存在する場合は`true`を返し、したがってルート計画が成功したことを示します。そうでない場合は`false`を返します。`dest`が無効な位置（グラフに存在しないノードインデックスを含む、または道路に沿った距離がゼロと道路の長さの間でない場合）である場合も`false`を返します。

`return_trip = true`を指定することは、ルートを計画するために帰り道の存在も必要です。
