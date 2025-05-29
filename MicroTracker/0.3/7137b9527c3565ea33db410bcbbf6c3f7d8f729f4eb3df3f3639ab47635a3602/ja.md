```
estimate_omega(x::AbstractVector, y::AbstractVector)
```

`x, y`データの最高周波数ピークを取得し、対応する`xf`を2で割って返します。

これは、`y`データが回転ごとに2つのピークを示す場合のローリングマイクロボットに対して機能します。データに応じて、これは`Angle`、`Major_m`、または`V`列である可能性があります。
