```
ECEFfromENU(origin, datum)
ECEFfromENU(origin::UTM, zone, isnorth, datum)
ECEFfromENU(origin::ECEF, lat, lon)
```

ローカル `ENU` 座標を `origin` を中心にグローバル `ECEF` 座標に変換する `Transformation` オブジェクトを構築します。このオブジェクトは、最大の効率のために、原点の ECEF 座標と緯度および経度の両方を事前にキャッシュします。
