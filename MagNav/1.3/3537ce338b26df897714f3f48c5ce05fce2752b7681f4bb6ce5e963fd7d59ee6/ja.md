```
get_map_val(map_map::Map, lat, lon, alt; α = 200, return_itp::Bool = false)
```

飛行経路に沿ったスカラー磁気異常マップ値を取得します。`map_map`は必要に応じて`alt`まで上方および/または下方に続けられます（ドレープマップを除く）。

**引数:**

  * `map_map`:    `Map` 磁気異常マップ構造体
  * `lat`:        緯度  [rad]
  * `lon`:        経度 [rad]
  * `alt`:        高度 [m]
  * `α`:          （オプション）下方継続のための正則化パラメータ
  * `return_itp`: （オプション）trueの場合、`itp_map`も返します

**戻り値:**

  * `map_val`: スカラー磁気異常マップ値
  * `itp_map`: `return_itp = true`の場合、マップ補間関数（`f(lat,lon)`または`f(lat,lon,alt)`）
