```
map_check(map_map::Map, path::Path, ind = trues(path.N))
```

与えられた地図上に緯度と経度のポイントがあるかどうかを確認します。

**引数:**

  * `map_map`: `Map` 磁気異常地図構造体
  * `path`:    `Path` 構造体、すなわち `Traj` 軌道構造体、`INS` 慣性航法システム構造体、または `FILTout` フィルタ抽出出力構造体
  * `ind`:     （オプション）選択されたデータインデックス

**戻り値:**

  * `bool`: true の場合、すべての `path`[`ind`] ポイントが `map_map` 上にあります
