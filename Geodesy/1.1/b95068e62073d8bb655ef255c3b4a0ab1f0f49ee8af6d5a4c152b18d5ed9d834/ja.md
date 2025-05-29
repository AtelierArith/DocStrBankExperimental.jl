```
ENUfromECEF(origin, datum)
ENUfromECEF(origin::UTM, zone, isnorth, datum)
ENUfromECEF(origin::ECEF, lat, lon)
```

グローバル `ECEF` 座標を `origin` を中心としたローカル `ENU` 座標に変換する `Transformation` オブジェクトを構築します。このオブジェクトは、最大の効率のために、原点の ECEF 座標と緯度および経度の両方を事前にキャッシュします。
