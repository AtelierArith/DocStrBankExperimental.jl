# Leaflet

[![](https://img.shields.io/badge/docs-stable-blue.svg)](https://JuliaGeo.github.io/Leaflet.jl/stable) [![](https://img.shields.io/badge/docs-dev-blue.svg)](https://JuliaGeo.github.io/Leaflet.jl/dev) [![CI](https://github.com/JuliaGeo/Leaflet.jl/actions/workflows/CI.yml/badge.svg)](https://github.com/JuliaGeo/Leaflet.jl/actions/workflows/CI.yml) [![codecov.io](http://codecov.io/github/JuliaGeo/Leaflet.jl/coverage.svg?branch=main)](http://codecov.io/github/yeesian/Leaflet.jl?branch=main)

JuliaのためのLeafletJSマップ。

このパッケージはWebIO.jlと統合されており、Blink.jl、Mux.jl、Jupyterノートブックなどの出力用にleafletマップをレンダリングします。

すべての[GeoInterface.jl](https://github.com/JuliaGeo/GeoInterface.jl)互換のジオメトリはレイヤーとして表示できます。

基本的な例として、GADMを使用して国境のシェープファイルをダウンロードし、CARTOの`:dark_nolabels`ベースレイヤーの上にプロットします。

```julia
using Leaflet, Blink, GADM
layers = Leaflet.Layer.([GADM.get("CHN").geom[1], GADM.get("JPN").geom[1]]; color=:orange); 
provider = Providers.CartoDB()
m = Leaflet.Map(; layers, provider, zoom=3, height=1000, center=[30.0, 120.0]);
w = Blink.Window(; body=m)
```

![](https://user-images.githubusercontent.com/4471859/275353261-0b1aa078-be0f-443c-a5d8-fc27a9a66cef.png)
