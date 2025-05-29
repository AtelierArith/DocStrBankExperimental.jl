地震位置データの可変型。

```
Earthquake(lat,lon,depth,local_mag,moment_mag)
```

緯度と経度はWGS84楕円体の度数を仮定します。深さはkm単位です。モーメントマグニチュードが指定されていない場合、Mw=0です。すべてのフィールドは::Float64です。
