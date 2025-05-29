```
max_pixrad(res::Resolution, ring)
max_pixrad(res::Resolution)
```

ピクセルの中心とその隅の間の最大角距離（ラジアン単位）を返します。`ring`が指定されている場合、結果は指定されたリングのすべてのピクセルに適用されます。そうでない場合は、球上のすべてのピクセルが考慮されます。
