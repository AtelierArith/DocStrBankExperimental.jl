```
fit(HDMR,@model(h ~ x1 + x2, c ~ x1),df,counts; <keyword arguments>)
```

HDMRを適合させますが、共変量行列の代わりにモデル式とデータフレームを取ります。詳細は[`fit(::HDMR)`](@ref)を参照してください。

左辺の`h`と`c`は、それぞれゼロと正のモデルを示します。
