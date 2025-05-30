```
onpick(f, fig/ax/scene, plots::AbstractPlot...)
```

マウスが `plots` のいずれかの上にあるときに `f(plot, idx)` を呼び出します。`idx` はインデックスで、例えば散布図の上にあるときは、ホバーしている要素のインデックスになります。
