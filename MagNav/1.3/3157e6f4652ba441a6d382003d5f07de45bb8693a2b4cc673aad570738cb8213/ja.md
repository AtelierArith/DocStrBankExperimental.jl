```
get_map_val(map_map::Map, path::Path, ind = trues(path.N);
            α=200, return_itp::Bool = false)
```

フライトパスに沿ったスカラー磁気異常マップの値を取得します。`map_map`は必要に応じて`alt`に対して上方および/または下方に続けられます。

**引数:**

  * `map_map`:    `Map` 磁気異常マップ構造体
  * `path`:       `Path` 構造体、すなわち `Traj` 軌道構造体、`INS` 慣性航法システム構造体、または `FILTout` フィルタ抽出出力構造体
  * `ind`:        （オプション）選択されたデータインデックス
  * `α`:          （オプション）下方続行のための正則化パラメータ
  * `return_itp`: （オプション）trueの場合、`map_itp`も返す

**戻り値:**

  * `map_val`: スカラー磁気異常マップの値
  * `map_itp`: `return_itp = true`の場合、マップ補間関数（`f(lat,lon)`または`f(lat,lon,alt)`）
