```
onpick(f, fig/ax/scene, plots::AbstractPlot...)
```

マウスが任意の `plots` の上にあるときに `f(plot, idx)` を呼び出します。`idx` はインデックスであり、例えば散布図の上にあるときは、ホバーされた要素のインデックスになります。
