```
(map_cache::Map_Cache)(lat::Real, lon::Real, alt::Real;
                      silent::Bool = true)
```

特定の位置でキャッシュされた地図値を取得します。

**引数:**

  * `map_cache`: `Map_Cache` 地図キャッシュ構造体
  * `lat`:       緯度  [ラジアン]
  * `lon`:       経度 [ラジアン]
  * `alt`:       高度  [メートル]
  * `silent`:    （オプション）trueの場合、出力は行われません

**戻り値:**

  * `map_val`: スカラー磁気異常地図値
