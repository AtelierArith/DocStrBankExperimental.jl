```
plotmap(m::OpenStreetMapX.MapData;
    roadwayStyle = OpenStreetMapXPlot.LAYER_STANDARD,
    width::Integer=600, height::Integer=600, use_plain_pyplot::Bool=false)
```

与えられた地図 `m` の `roadways` をプロットします。

幅は `width` に設定され、高さは `height` に設定されます。 `width` または `height` のいずれか一方のみが設定されている場合、もう一方はバウンディングボックスのアスペクト比を保持するように設定されます。 `km` パラメータを使用すると、メートルの代わりに地図のキロメートルスケールを持つことができます。

デフォルトのプロットバックエンドは `Plots.jl` で定義されているものですが、 `use_plain_pyplot` が `true` に設定されている場合、Plots.pythonplot() が呼び出されてPythonPlotバックエンドに切り替えられます（このオプションは非推奨であり、通常バックエンドはこの関数の外で変更されるべきです）。

さらなるプロットの更新に使用できるオブジェクトを返します。
