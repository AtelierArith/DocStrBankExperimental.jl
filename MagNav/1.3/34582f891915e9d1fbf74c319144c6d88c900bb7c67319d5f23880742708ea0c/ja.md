```
map_trim(map_map::Map, path::Path;
         pad::Int          = 0,
         zone_utm::Int     = 18,
         is_north::Bool    = true,
         map_units::Symbol = :rad,
         silent::Bool      = true)
```

`path`から遠く離れた大きな領域を削除することによって地図をトリミングします。これはエッジ効果エラーを引き起こすため、上方継続の前には使用しないでください。トリミングされた磁気異常マップ構造体を返します。

**引数:**

  * `map_map`:   `Map` 磁気異常マップ構造体
  * `path`:      `Path` 構造体、すなわち `Traj` 軌道構造体、`INS` 慣性航法システム構造体、または `FILTout` フィルタ抽出出力構造体
  * `pad`:       (オプション) マップの端に沿った最小パディング（グリッドセル）
  * `zone_utm`:  (オプション) UTMゾーン、`map_units = :utm` の場合のみ使用
  * `is_north`:  (オプション) trueの場合、マップは北半球にあり、`map_units = :utm` の場合のみ使用
  * `map_units`: (オプション) マップのxx/yy単位 {`:rad`,`:deg`,`:utm`}
  * `silent`:    (オプション) trueの場合、出力は表示されません

**返り値:**

  * `map_map`: `Map` 磁気異常マップ構造体、トリミング済み
