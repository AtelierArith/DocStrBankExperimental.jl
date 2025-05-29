```
draw_curve(pts::Array{Complex{T},1}, closed::Bool = true; opts...) where {T}
```

`draw_curve(plist)` は、1次元の複素数リストである `plist` の点を通る閉じた曲線を描画します。開いた曲線には `draw_curve(plist,false)` を使用してください。
