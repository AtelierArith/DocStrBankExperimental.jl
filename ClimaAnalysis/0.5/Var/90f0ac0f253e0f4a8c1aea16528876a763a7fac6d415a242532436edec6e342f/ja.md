```
integrate_lon(var::OutputVar)
```

経度に沿って、一次スキームを用いて`var`内の`data`を積分します。`data`は経度に沿って離散化されている必要があります。

点が等間隔である場合、各点はセルの中点に対応すると仮定され、中点法を用いた長方形の積分が行われます。それ以外の場合、積分は左端点を用いた長方形の積分が行われます。経度の単位は度である必要があります。

`var.data`内のすべての`NaN`は、積分時にゼロとして扱われます。
