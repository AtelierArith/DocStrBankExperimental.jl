```
snapshot(;
    fname = :png,
    cb = missing,
    scalefactor = 1.0,
    addmarker = true)

snapshot(fname, cb, scalefactor)
-> finished snapshot drawing, for display
```

スナップショットを取り、'fname' 名とサフィックスで保存します。これは、現在の描画が記録面であることを要求します。同じ記録面上で描画を続けることができます。

スナップショットを描画として返します。

### 引数

`fname` ファイル名またはシンボル、[`Drawing`](@ref)を参照

`cb` クロップボックス::BoundingBox - 中にあるものがスナップショットにコピーされます

`scalefactor` スナップショットの幅/クロップボックスの幅。同様に高さも。

`addmarker` `addmarker` に関する詳細は `Luxor._adjust_background_rects` のヘルプを参照してください。

```
?Luxor._adjust_background_rects
```

### 例

```julia
snapshot()
snapshot(fname = "temp.png")
snaphot(fname = :svg)
cb = BoundingBox(Point(0, 0), Point(102.4, 96))
snapshot(cb = cb)
pngdrawing = snapshot(fname = "temp.png", cb = cb, scalefactor = 10)
```

最後の例は、1024 x 960 ピクセルの png 描画をストレージに返し、書き込みます。
