```
setlight(bridge::PhilipsHueBridge, light::Int, col::ColorTypes.Colorant)
setlight(B, 1, Colors.RGB(0.75, 0.25, 0.75))
setlight(B, 1, colorant"Pink")
```

Colors.jlスタイルの色を使用してライトの色を設定します。（`using Colors`が必要な場合があります。）
