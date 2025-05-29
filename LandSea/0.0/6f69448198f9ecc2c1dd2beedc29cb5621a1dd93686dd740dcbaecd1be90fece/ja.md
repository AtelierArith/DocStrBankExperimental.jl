```
LandSeaData
```

LandSeaデータセットの抽象スーパタイプ。すべての`LandSeaData`タイプは以下のフィールドを含みます：

  * `lon` - Land-Seaデータセットの経度ポイントを含むベクター
  * `lat` - Land-Seaデータセットの緯度ポイントを含むベクター
  * `lsm` - Land-Seaマスクに関するデータを含む配列。1は陸、0は海、NaNはGeoRegionの範囲外です。
